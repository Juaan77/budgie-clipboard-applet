configurationData = configuration_data()
configurationData.set('PACKAGE_NAME', meson.project_name())
configurationData.set('LOCALE_DIR', LOCALE_DIR)
configure_file(input: 'config.h.in', output: 'config.h', configuration: configurationData)

install_data('ClipboardManager.plugin', install_dir: LIB_INSTALL_DIR)

ClipMgrSources = [
'ClipboardManagerApplet.vala'
]

ClipMgrDependencies = [
dependency('gtk+-3.0'), 
dependency('budgie-1.0'),
dependency('libpeas-gtk-1.0'),
meson.get_compiler('c').find_library('m', required: false)
]

ClipMgrValaArgs = [
'--pkg=config', 
'--vapidir=' + VAPI_DIR, 
'--target-glib=2.38',
]

ClipMgrCArgs = [
'-include', 
'config.h',
'-lm'
]

shared_library(
    'clipmgr', 
    ClipMgrSources, 
    dependencies: ClipMgrDependencies, 
    vala_args: ClipMgrValaArgs, 
    c_args: ClipMgrCArgs, 
    install: true, 
    install_dir: LIB_INSTALL_DIR
)
