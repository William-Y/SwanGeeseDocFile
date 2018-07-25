## SimpleITK-Activiz .NET Win10环境配置过程

### Simple ITK 配置（IDE:Visual Studio 2017）

1. 下载源码并解压缩*（x64 version）* [源蛤网址](https://sourceforge.net/projects/simpleitk/files/SimpleITK/1.1.0/CSharp/SimpleITK-1.1.0-CSharp-win64-x64.zip/download)
2. 在Visual Studio中打开解决方案属性，点入配置管理器，将所建项目的平台与活动解决方案平台改为x64。
3. 在引用处点击右键，点击添加引用，进入浏览标签页，将解压缩文件夹中的SimpleITKCSharpManaged.dll添加入引用，勾选后确定。
4. 将SimpleITKCSharpNative.dll添加至探测路径，即xaml代码所在处。



### Activiz .NET 配置*（IDE: Visual Studio 2017）* 

1. 下载压缩包Activiz .NET并解压缩*（x64 version）*[Git网址](https://github.com/William-Y/SwanGeeseDocFile) 

2. 该压缩包为从Visual Studio 包管理器中下载的Activiz .NET x64包中提取出的dll文件集。

3. 在Visual Studio中打开解决方案属性，点入配置管理器，将所建项目的平台与活动解决方案平台改为x64。

4. 在引用处点击右键，点击添加引用，进入浏览标签页，将解压缩文件夹中的Kitware.mummy.Runtime.dll 与 Kitware.VTK.dll添加入引用，勾选后确定。

   