# -*- python -*-
# $Id$
# Authors: Joanne Bogart <jrb@slac.stanford.edu>
# Version: xmlBase-05-05-08
Import('baseEnv')
Import('listFiles')
progEnv = baseEnv.Clone()
libEnv = baseEnv.Clone()

if baseEnv['PLATFORM'] == "win32":
    libEnv.Tool('xmlBaseLib', depsOnly = 1)

xmlBaseLib = libEnv.SharedLibrary('xmlBase', [ 'src/Dom.cxx', 'src/IFile.cxx', 'src/XmlErrorHandler.cxx', 'src/XmlParser.cxx', 'src/EResolver.cxx', 'src/docMan/DocMan.cxx'])

progEnv.Tool('xmlBaseLib')
entity_test = progEnv.Program('entity_test',[ 'src/test/entity_test.cxx'])
test_xmlBaseBin = progEnv.Program('test_xmlBase',[ 'src/main.cxx'])
test_memBin = progEnv.Program('test_mem',[ 'src/test/test_mem.cxx'])
test_IFileBin = progEnv.Program('test_IFile',[ 'src/test/test_IFile.cxx'])
test_writeBin = progEnv.Program('test_write',[ 'src/test/test_write.cxx'])

progEnv.Tool('registerTargets', package = 'xmlBase',
             libraryCxts = [[xmlBaseLib, libEnv]],
             testAppCxts = [[entity_test, progEnv], [test_xmlBaseBin,progEnv],
                            [test_memBin, progEnv], [test_IFileBin,progEnv],
                            [test_writeBin, progEnv]],
             includes = listFiles(['xmlBase/*.h', 'xmlBase/docMan/*.h']),
             xml = listFiles(['xml/*'], recursive = True))




