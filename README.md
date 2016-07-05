# DLPluginDemo
android动态加载apk插件式开发

项目中主要涉及宿主项目跟插件项目的开发过程测试，项目采用DL框架，可支持附带activity,service等插件的加载。
mylibrary为DL框架，宿主项目直接引用就即可。插件项目开发时最好把mylibrary制成jar文件，开发时直接引用jar包，
打包成apk时需要排除将mylibrary.jar打入apk内，在build.gradle中添加以下代码（extra-libs为mylibrary.jar存放路径）
dependencies {
    provided fileTree(dir: 'extra-libs', include: ['*.jar'])
}
避免宿主项目跟插件项目都存在该jar包引发错误。

（dlplugintest为插件项目，在添加上述代码后编译运行，如果直接安装apk后会报错，这是由于jar包没打进来，把生成的apk放置在手机的dlplugin
文件夹下，运行宿主项目即可）

