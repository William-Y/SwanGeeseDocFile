[TOC]

注：目前仅打框架、记录重要信息。

# 软件简介

见[官网的说明](http://www.itksnap.org/docs/viewtutorial.php?chapter=TutorialSectionIntroduction)。

# 编译、安装与运行

## 编译

见[这里](http://shengliangd.coding.me/archivers/build-ITK-SNAP)。

## 安装

可以直接安装二进制包，不再赘述。

## 运行

直接执行可执行文件即可。

# 软件使用说明



- ###### 打开文件 *（File）*

  ​	右上角 *File* 中选择 *Open Main Image（快捷键Ctrl+G）* 浏览文件地址进行选定，也可以通过 *Recent Main Image*  选择文件地址，或者在主显示栏上方的 *Recent Image* 中通过影像缩略图进行打开。

  ​	打开文件后在软件的主显示栏会显示图片的三视图以及分割块的立体形状，可用鼠标滚轮调整光标所在视图处的图像在图片集中的位置。

  

- ###### 图像编辑 *（Edit）*

  ​	itk-snap中对影像标注的方法有三种，分别为多边形分割 *（Polygon Segmentation）*，毛刷分割 *（Paintbrush）* 和半自动分割 *（Auto-Segmentation）*。

  ​	分割时可使用不同的Label代表不同的分割块，以此起到区分作用。 

  1. 多边形分割 *（Polygon Segmentation）*

  ​	多边形分割中有两种分割区域选定模式，一为*Smooth Curve* ，一为*Polygon* 。

  ​	 *Smooth Curve*模式中，使用者可使用鼠标于图中做出任意形状的封闭曲线，并以此为依据做出分割区域。

  ​	 *Polygon*模式中，使用者使用鼠标在图中给出多个点，并将各点依次连接形成封闭多边形，以此为依据做出分割区域。*Segmentation Length* 为连续作画时的最长大小。

  ​	作画完成后，若曲线末端未相互连接，可点击图像下方的*complete*用于封闭图形，而后点击*accept* 进行标注，标注前可勾选*Invert polygon* 用以标注封闭多边形外部。

  

  2. 毛刷分割 *（Paintbrush）*

  ​	毛刷分割需要使用者自行涂刷标注区域。涂刷风格有方形与圆形，且可选择毛刷大小。

  ​	毛刷分割中还有一种区域为自适应涂写，可自动识别毛刷所在区域中的灰度值，并且可以自行识别边界进行标注。

  ​	在*Inspector* 中还有几个毛刷选项：3D表示标注时会自动识别所有图片在当前选定区域中的灰度值，并且同步进行识别标注。*Isotropic* 为各向同性处理，*（尚未摸清）*。 *Cursor chases brush* 表示当点击鼠标进行标注时，图像上的十字交叉点会自动跳至光标所在处。

  ​	毛刷分割中点击右键可清除当前选定区域的标注，可用于修改各个算法中生成的标注区域。

  

  3. 半自动分割 *（Auto-Segmentation）*

   半自动分割的使用分为几步：

     a. 在*Inspector* 区域中选定ROI *（Region of  Interest）*，即图像中出现的红色虚线所表示区域。勾选 *Resample ROI* 表示在分割时可重新选定标注区域；勾选 *Initialize with currer segmentation*  表示使用当前标注区域作为最后区域生长的种子。

     b. 点击*Segment 3D* ，进入分割模式选项。在软件框右方出现预分割阶段1 *（Presegmentation Stage 1）*，在Action中可选择预分割模式 *（Presegmentation mode）*， 该软件共有四种预分割模式，阈值模型 *（Thresholding）*，分类模型 *（Classification）*，聚类模型 *（Clustering）* 以及边缘吸引模型 *（Edge Attraction）*。

     选择完模型后，则需要针对不同的模型对参数进行不同的处理。

     1. 阈值模型 *（Thresholding）*

         可调整阈值的大小以及上下阈值模式

     2. 分类模型 *（Classification）*

         需选择不同类别所代表的区域，点击*Train Classifier* 进行训练。	

     3. 聚类模型 *（Clustering）*

         需选择聚类数以及迭代次数

     4. 边缘吸引模型 *（Edge Attraction）*

         需调整平滑因子

  ​     调整参数后，在图像显示区域右上角有一张表示预处理过后得到的图像，称为*Speed Image*， 该图为预处理过后生成的用于后阶段的标注区域生长的基底。

     c.  选择分类模型，初步调整参数后，进入阶段2。

   	在预分割阶段2 *（Presegmentation Stage 2）* 中，点击*Add Bubble at Cursor*，在交叉线交点添加*Bubble*，并以此作为图像生长的种子，在按钮下方可调整*Bubble*大小。	

  ​    d. 点击*Next* 进入预分割阶段3 *（Presegmentation Stage 3）*， 可在 *Set Parameters ...* 可设置生长算法的参数。

  ​	设置完参数后，点击下方▶按钮进行生长。其右边的按钮表示进行一次迭代，左边的按钮表示恢复原状态。

  ​	在生长完成后，点击下方*Finish*按钮完成自动标注，标注数据会显示在图像中。

  ​	在此三种标注方法之后，点击图像显示区域的左下角的*update*按钮可将标注块的3D影像图显示在第三块图像区域中。

  

- ###### 分割数据 *（Segmentation）*

  ​	对于加载入图像显示区域的图像，可以通过*Segmentation* 菜单中的*Open Segmentation* 工具或者*Recent Segmentation* 直接载入图像的标注数据。

  ​	对于已标注的图像数据，也可以通过*Segmentation*菜单中的*Save Segmentation Image* 工具保存或者*Unload Segmentation* 卸载图像数据的标注数据。

  ​	对于*Label* 数据亦可通过*Import Label Description*载入标签，*Export Label Description* 保存标签。

  ​	对于已分割好的数据，可以在*Segmentation*菜单中的*Volumes and Statistics*获取各个标签块的体积，像素数，亮度等数据。

  ​	

- ###### 工作空间 *（Workspace）*

  ​	该菜单用于加载 *（Open Workspace & Recent Workspace）* 与保存 *（Save Workspace & Save Workspace as）* 工作空间。

  

- ###### 工具 *（Tools）*

  ​	 *Tools*菜单下的*Layer Inspector* 选项中包含了影像数据的各种属性，如对比度 *（Contrast）*，颜色图 *（Color Map）* 以及元数据 *（Metadata）*。该选项下的三个选项分别指向上述三种属性。

  ​	选项*Active  Main Tool* 为软件左沿*Toolbox*中的*Main Toolbar*中包含功能，分别为交叉线 *（Crosshair Tool）*，缩放模式 *（Zoom/Pan Mode）*，多边形分割工具 *（Polygon Drawing Tool）*，毛刷分割工具 *（Paintbrush Mode）*， 半自动分割工具 *（Active Contour Segmentation Mode）*，标注工具 *（Annotation Tool）*（用于对图上的各种特殊区域进行测量，注释等）。

  ​	选项*Active 3D Tools* 是用于对生成的3D影像进行处理的工具箱，位于*Toolbox*的最底端。

  ​		选定 *3D Trackball Tool*可切换3D图的视角与缩放。

  ​		选定*3D Crosshair Tool*，点击鼠标左键可调整三轴交叉点的位置。

  ​		选定*3D Scalpel Tool*，将Label切换为与当前3D影像不同的Label，可在3D影像表面做出标记。

  ​		选定*3D Spray Paint Tool*，点击鼠标左键选择切平面，可得到一个法向量一定的可平移平面。

  ​	选项*Reorient Image*用于重制图像显示区域的三视图。

# 软件结构与执行流程分析

## 半自动化图像分割流程

1. 使用四种预处理算法之一进行预处理；
2. 设定初始区域；
3. 使用 level set 算法使初始区域生长至适当范围。

# 核心算法分析

[这里](http://shengliangd.coding.me/archivers/ITK-SNAP-Core-Algorithm)。

# 程序运行时行为特征分析



# 应用优化方案

算法优化，提高其自动化程度，直至能够全自动标注图像中的肿瘤。



