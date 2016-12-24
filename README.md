NDK Samples [![Build Status](https://travis-ci.org/googlesamples/android-ndk.svg?branch=master)](https://travis-ci.org/googlesamples/android-ndk) [![Build status](https://ci.appveyor.com/api/projects/status/48tbtqwg4heytmnq?svg=true)](https://ci.appveyor.com/project/proppy/android-ndk)
===========

The origin README, please move to : https://github.com/googlesamples/android-ndk

---

### Sample try: hello-jni

Simple to running it in Android Studio, just "Open" project on the  `other-builds/ndkbuild/hello-jni`.

#### Architecture:

As you can see there are only `Android.mk` and `Application.mk` implmentation on the `other-builds/ndkbuild/hello-jni`, and others(`java`、`cpp`、etc) are all in the `hello-jni`, which is declared in the following files:

##### [other-builds/ndkbuild/hello-jni/app/build.gradle](https://github.com/Jacksgong/android-ndk/blob/master/other-builds/ndkbuild/hello-jni/app/build.gradle):

```groovy
apply plugin: 'com.android.application'

// pointing to cmake's source code for the same project
def REMOTE_PROJ_ROOT = '../../../../' + rootProject.getName() + '/' +
                        project.getName() + '/src/main'
android {
  ...

    externalNativeBuild {
        ndkBuild {
            path 'Android.mk'
        }
    }
    sourceSets {
        main {
            manifest.srcFile "${REMOTE_PROJ_ROOT}/AndroidManifest.xml"
            java.srcDirs = ["${REMOTE_PROJ_ROOT}/java"]
            res.srcDirs = ["${REMOTE_PROJ_ROOT}/res"]
        }
    }

    ...
}
...

```

[other-builds/ndkbuild/hello-jni/app/Android.mk](https://github.com/Jacksgong/android-ndk/blob/master/other-builds/ndkbuild/hello-jni/app/Android.mk):

```groovy
...

JNI_SRC_PATH := $(LOCAL_PATH)/../../../../hello-jni/app/src/main/cpp

...

LOCAL_SRC_FILES := $(JNI_SRC_PATH)/hello-jni.c

...
```


License
-------

Copyright 2015 The Android Open Source Project, Inc.

Licensed to the Apache Software Foundation (ASF) under one or more contributor
license agreements.  See the NOTICE file distributed with this work for
additional information regarding copyright ownership.  The ASF licenses this
file to you under the Apache License, Version 2.0 (the "License"); you may not
use this file except in compliance with the License.  You may obtain a copy of
the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the
License for the specific language governing permissions and limitations under
the License.

[LICENSE](LICENSE)

[0]: https://developer.android.com/ndk
