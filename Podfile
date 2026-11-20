# MacDown requires macOS 11 (Big Sur) or later, the first release that runs
# natively on Apple Silicon. Builds are universal (arm64 + x86_64).
MACDOWN_DEPLOYMENT_TARGET = '12.0'

platform :osx, MACDOWN_DEPLOYMENT_TARGET

source 'https://github.com/MacDownApp/cocoapods-specs.git'  # Patched libraries.
source 'https://cdn.cocoapods.org/'

project 'MacDown.xcodeproj'

inhibit_all_warnings!

target "MacDown" do
  pod 'handlebars-objc', '~> 1.4'
  pod 'hoedown', '~> 3.0.7', :inhibit_warnings => false
  pod 'JJPluralForm', '~> 2.1'
  pod 'LibYAML', '~> 0.1'
  pod 'M13OrderedDictionary', '~> 1.1'
  pod 'MASPreferences', '~> 1.3'
  pod 'PAPreferences', '~> 0.5'
  pod 'Sparkle', '~> 2.6'
end

target "MacDownTests" do
  pod 'PAPreferences', '~> 0.5'
end

target "macdown-cmd" do
  pod 'GBCli', '~> 1.1'
end

post_install do |installer|
  installer.pods_project.build_configurations.each do |config|
    config.build_settings['MACOSX_DEPLOYMENT_TARGET'] = MACDOWN_DEPLOYMENT_TARGET
  end
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      # Old podspecs pin 10.8, which current Xcode no longer supports (and
      # which would require the removed libarclite). Pin every pod to ours.
      config.build_settings['MACOSX_DEPLOYMENT_TARGET'] = MACDOWN_DEPLOYMENT_TARGET
      # Let Xcode decide the architectures (arm64 + x86_64 for release).
      config.build_settings.delete('ARCHS')
      config.build_settings.delete('VALID_ARCHS')
      config.build_settings.delete('EXCLUDED_ARCHS')
    end
  end
end
