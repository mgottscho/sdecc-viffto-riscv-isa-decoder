#!/bin/python

import platform
os_info = platform.platform()
print os_info

if os_info.find('Linux') >= 0 or os_info.find('Darwin') >= 0: # Linux or Mac build
    env = Environment()
    env.Replace(CXX = 'x86_64-linux-gnu-g++-5')
    env.Append(CXXFLAGS = '-Wall -Wpedantic -Wsign-compare -O3 -std=c++14')
    env.Append(CPPPATH = ['src',])
elif os_info.find('Windows') >= 0:
    env = Environment(MSVC_USE_SCRIPT = 'C:\\Program Files (x86)\\Microsoft Visual Studio 14.0\\VC\\bin\\x86_amd64\\vcvarsx86_amd64.bat')
    env.Append(CPPFLAGS = ['/c','/nologo','/W3','/WX-','/O2'])
else:
    print 'unknown platform, exiting'
    exit(1)
sources = [
    Glob('src/riscv-*.cc'),
    'src/main.cc'
]

defaultBuild = env.Program(target = 'riscvdecode', source = sources)
Default(defaultBuild)