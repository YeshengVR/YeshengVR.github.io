# Unity

Unity3D建模软件学习

## Unity3D窗口介绍

- Game：游戏运行窗口
- Scene：场景编辑窗口
- Hierarchy：场景物体列表窗口
- Project：项目资源列表窗口
- Inspector：属性编辑列表窗口
- 其他常用调节窗口

Unity语言使用C#进行开发

- 简单易用
- 开发效率高
- 价格便宜
- 新手居多

Scene场景面板

- 提供设计游戏界面的可视化面板
- 常用快捷键
  1. 按下鼠标滚轮拖动场景，滑动滚轮缩放场景。
  2. 鼠标右键旋转场景，点击“![手](F:\md笔记文件\Unityimg\手.png)”后，通过左键移动场景。
  3. 点击右键同时按下W/S/A/D/Q/E键可实现场景漫游。
  4. 在Scene面板选中物体后按F键，或在Hierarchy面板双击物体，可将物体设置为场景视图的中心。
  5. 按住alt键同时通过鼠标左键围绕某物体旋转场景，鼠标右键缩放场景。

Hierarchy层次面板

- 显示当前场景中所有游戏对象的层级关系。
- 包含了当前场景的游戏对象(GameObject)，其中一些是资源文件的案例，如3D模型和其他预制组件的实例。

Game游戏面板

- 预览游戏运行后的界面

Inspector检视面板

- 显示当前选定游戏对象附加的组件及其属性信息。
- 为重要游戏物体选择图标

**Transform**:每一个物体都有的属性，控制物体的旋转，移动与缩放。

- Position：距离 	x轴值：离x轴原点距离；y轴值：离y轴原点的距离；z轴值：离z轴原点的距离
- Rotation：旋转     x轴：沿x轴旋转多少度，y轴：沿y轴旋转多少度；z轴：沿z轴旋转多少度
- Scale：缩放比例      x轴值：沿x轴缩放多少倍；y轴值：沿y轴缩放多少倍；z轴值：沿z轴缩放多少倍

**移动场景Q      移动物体W   旋转物体E   缩放物体R**

**顶点吸附**：选择物体后按住V键，定位定点，再拖拽到目标物体某个顶点上。备注：先松V键

物体：Cube：正方体

Plane：平面，一个片面

变换切换

- 左边是改变游戏对象的轴心点
  - Center:设置轴心点在物体中心
  - Pivot:使用物体本身的轴心

- 右边是改变物体的坐标，Global:世界坐标；Local：自身坐标

Scene：场景

Intro：介绍

Diagnose：诊断

玩家体验场景的常用方式如下：

![](F:\md笔记文件\Unityimg\游戏流程.webp)

在游戏开发方面，通常称这为“游戏流程”。

也可适当进行些操作改成如下情况

![](F:\md笔记文件\Unityimg\游戏流程改.webp)

Global：世界的 Local：自身

播放控件从左到右依次是预览游戏，暂停游戏，逐帧播放。

### 视图

ISO：正交观察模式
Persp：透视观察模式(近大远小)
试图角度：上下左右前后

![](F:\md笔记文件\Unityimg\Persp.png)

### 坐标

坐标：X红色、Y绿色、Z蓝色
世界坐标：整个场景的固定座标、不随物体旋转而改动
本地坐标：物体自身坐标，随旋转而改变。

### Scene

一组相关联的游戏对象的集合，通常游戏中每个关卡就是一个场景，用于展现当前关卡中的所有物体。

### GameObject

- 运行时出现在场景中的游戏物体。例如：人物、地形、数目....

- 是一种容器，可以挂载组件

- 父、子物体

  在Hierarchy面板中，将一个物体拖拽到另外一个物体中。子物体将继承父物体的移动，旋转和缩放属性，但子物体不影响父物体。

### 组件Component

- 是游戏对象的功能模块。
- 每个组件都是一个类的实例。
- Transform变换组件：决定物体位置、旋转、缩放比。
- Mesh Filter 网格过滤器：用于从资源中获取网格信息。
- Mesh Renderer 网格渲染器：从网格过滤器中获得几何形状，再根据变化组件定义的位置进行渲染。
- 网格过滤器于网格渲染器联合使用，使模型显示到屏幕上。

#### 练习：创建子弹

由两个Capsule(胶囊),1个Cylinder(圆柱体)组成。

![](F:\md笔记文件\Unityimg\子弹.png)

基本流程图

![](F:\md笔记文件\Unityimg\基本流程.png)

### Material

- 材质：物体的质地，指色彩、纹理、光滑度、透明度、反射率、折射率、发光度等。实际就是Shader的实例。
- Shader着色器：专门用来渲染3D图形的技术，可以使纹理以某种方式展现。实际就是一段嵌入到渲染管线中的程序，可以控制GPU运算图像效果的算法。
- Texture纹理：附加到物体表面的贴图。

#### Readering Mode

- 渲染模式

  -- Opaque 不透明，默认选项

  -- Transparent 透明，用于半透明和全透明物体，如玻璃。

  -- Cutout 镂空，用于完全透明或完全不透明物体，如栅栏。

  -- Fade 渐变，用于需要淡入淡出的物体。可以完全透明。

#### Main Maps

- Albedo 基础贴图 ：决定物体表面纹理与颜色。

- Metallic 金属 ：使用金属特性模拟外观。

- Specular 镜面反射：使用镜面特性模拟外观

- Smoothness 光滑度：设置物体表面光滑程度

- Normal Map 法线贴图：描述物体表面凹凸程度。

- Emission 自发光：控制物体表面自发光颜色和贴图。

  -- None 不影响环境
  -- Realtime 实时动态改变
  -- Backed 烘焙生效

- Tiling 平铺：沿着不同的轴，纹理平铺个数。

- Offset 偏移：滑动纹理。

纹理、着色器与材质的关系

![](F:\md笔记文件\Unityimg\纹理、着色器与材质的关系.png)

### 物理着色器

- 基于物理特性的Shader是Unity 2.x的重大革新之一，所谓物理着色器(Physically Based Shadging，PBS)就是遵从物理学的能量守恒定律，可以创建出在不同光照环境下都接近真是得效果。

### 摄像机Camera

- 附加了摄像机Camera组件的游戏对象
- 向玩家捕获和显示世界的设备
- 场景中摄像机的数量不受限制

#### 组件

- Transform 变化组件
- Camera 摄像机：向玩家捕获和显示世界
- Flare Layer 耀斑层：激活可显示光源耀斑
- GUI Layer ：激活可渲染二维GUI元素
- Audio Listener 音频监听器 ：接受场景输入的音频源Audio Source 并通过计算机的扬声器播放声音。

#### 属性

- Clear Flags 清除标识：决定屏幕的空白部分如何处理

  Skybox 天空盒：空白部分显示天空盒图案

  - 天空盒是围绕整个场景的包装器，用于模拟天空的材质。

  - 天空盒材质种类：6Sided，Procedural，Cubemap。

    - 6Sided属性

      - Tint Color色彩
      - Exposure 亮度
      - Rotation 旋转

    - Procedural

      - Sun太阳模式

        -- None 没有
        -- Simple 简单
        --Hight Quality 高质量

      - Atmoshpere Thickness 大气层厚度

      - Ground 地面颜色

      - 如果为Environment Lighting 的Sun属性设置一个平行光，场景中会根据平行光角度自动创建太阳，并且位置随平行光旋转而改变。如果不设置，系统将默认选择场景中最亮的平行光。

  使用天空盒

  - 方法一：摄像机添加组件Skybox，设置Clear Flags 属性为Skybox。

  - 方法二：光照窗口

    Window - Lighting - Environment Lighting -- Skybox 可作为反射源将天空色彩反射到场景中物体。(新版本在Window- Redering - Lighting Settings --Environment Lighting  )

  solid Color 纯色：空白部分显示背景颜色

  Depth Only 仅深度：画中画效果时，小画面摄像机选择该项可清楚屏幕空部分信息只保留物体颜色信息。

  Don‘t Clear 不清除：不清除任何颜色或深度缓存。(容易花屏，一般不用)

- Background 背景：所有元素绘制后，没有天空盒的情况下，剩余屏幕的颜色。

- Culling Mask 选择遮蔽层：选择要照射的层Layer。

  Unity中任何游戏对象都有Tag (标记)以及Layer(层级)
  看不见的Unity就不会进行渲染

- Perspective：透视的；Orthographic：正交的(忽略了纵深的轴)

- Field of View ：控制镜头拉近拉远；如果是2D的则是size的变化

- Clipping Planes（剪裁面）：  Near：可视距离   Far：

- Viewport Rect： W：显示的宽；H显示的高（0-1之间的数值；1代表百分之百）X；Y(0-1之间摄像机在哪一块区域显示)

选择任何物品(摄像机)按ctrl+shift+f可以快速地把(物品)摄像机定位到某一位置。

### 练习：制作游戏场景小地图

1. 创建游戏主角Player

   子物体包括：主摄像机，地图标记。

2. 地图标记PleneMark

   创建物体Plane，材质mt_PlayerMark，并指定颜色为蓝色，纹理为mark

3. 创建敌人Enemy，并添加地图标记(红色)

4. 为所有地图标记指定层Mark

5. 地图摄像机 MapCamera

   设置属性：Clear Flags   Culling Mask  Projection  Size    Viewport Rect    Depth

## 渲染管线

- 图形数据在GPU上经过运算处理，最后输出到屏幕的过程。（在GPU上即显卡上。）

![](F:\md笔记文件\Unityimg\渲染管线.png)

Draw Call现在又称作：Batches。点击Game面板的Stats即可查看Batches数量。每帧要渲染的次数。
在不考虑光照的情况下，1个物体一个Batches。考虑光照就复杂多了。

### 定点处理：

- 接受模型顶点数据。
- 坐标系转换。

### 图元装配

- 组装面：连接相邻的顶点，绘制为三角形面

### 光栅化

- 计算三角形面上的像素，并为后面着色阶段提供合理的插值参数

### 像素处理

- 对每个像素区域进行着色。
- 写入到缓存中。

### 缓存

- 一个存储像素数据的内存块，最重要的缓存是帧缓存与深度缓存。
  - 帧缓存：存储每个像素的色彩，即渲染后的的图像。帧缓存常常在显存中，显卡不断读取并输出到屏幕中。
  - 深度缓存 z-buffer:存储像素的深度信息，即物体到摄像机的距离。光栅化时便计算各像素的深度值，如果新的深度值比现有值更近，则像素颜色被写到帧缓存，并替换深度缓存。

## Occlusion Culling

- **即使遮挡剔除** Instant Occlusion Culling
- 遮挡剔除：当物体被送进渲染流水线之前，将摄像机视角内看不到的物体进行剔除，从而减少了每帧渲染数据量，提高渲染性能。

### 步骤

1. 创建层
2. 为游戏物体指定层(将参与遮挡剔除)与标签(将自动附加IOClod脚本)
3. 物体添加碰撞器Collider组件
4. 摄像机附加脚本IOCcam

## LOD

**多细节层次Levels of Detail**

LOD技术根据物体模型的节点在显示环境中所处的位置和重要度，决定物体渲染的资源分配，降低非重要物体的面数和细节度，从而获得高效率的渲染运算。

## 预制件

域之间是一种特殊类型的组件，，它可以将完全配置的GameObject保存到项目中以供重复使用。可以在场景甚至其他项目之间共享这些资产。无需在此进行配置。
将对象从“层次结构”拖到“项目”窗口中时，将自动创建预制件。
层次结构中存在预制件时，将以蓝色文本和蓝色立方体表示。

将对象转换为Prefab时，将在“转换”值上方添加一组新的按钮。![](F:\md笔记文件\Unityimg\预制件.webp)

预制件可以在创建后进行编辑。可以按每个对象编辑Prefab，可以为单个目的更改Prefab的单个实例，还可以将这些更改应用于Prefab的所有实例。

- Revert All：全部还原，将还原替代列表中的所有更改。
- Apply All：全部应用，按钮将对选定的预制件进行的所有更改应用于所有其他现有实例以及项目窗口中的原始实例。

## 光照系统

### Global Illumination

- 简称GI，即全局光照
- 能够计算直接光、间接光、环境光以及反射光的光照系统。
- 通过GI算法可以使渲染出来的光照效果更为真实丰富。

#### 直接光照

- 从光源直接发出的光，通过Light组件实现。

- Type类型：灯光对象的当前类型

  --Directional Light 平行光：平行发射光线，可以照射场景里所有物体，用于模拟太阳。

  --Point Light 点光源：在灯光位置上向四周发射光线，可以照射其范围内的所有对象，用于模拟灯泡。

  --Spot Light 聚光灯：在灯光位置上向圆锥区域内发射光线，只有在这个区域内的物体才会受到光线照射，用于模拟探照灯。

  --Area Light区域光：由一个面向一个方向发射光线，只照射该区域内物体，仅烘焙时有效，用在光线较为集中的区域。(极其消耗性能)

- Range 范围：光从物体的中心发射的范围。仅适用于点光源和聚光灯。

- Spot Angle 聚光角度：灯光的聚光角度。只适用于聚光灯。

- Color 颜色：光线的颜色。

- Intensity 强度：光线的明亮程度。

- Culling Mask 选择遮蔽层：选择要照射的层Layer。

#### 环境光照

- 作用于场景内所有物体的光照，通过Environment Lighting中Ambient控制

- Ambient Source 环境光源

  --Skybox通过天空盒颜色设置环境光照

  --Gradient 梯度颜色

  Sky天空颜色、Equator地平线颜色、Ground地面颜色

  --Ambient Color 纯色

- Ambient Intensity 环境光强度

- Ambient GI 环境光GI模式

  --Realtime 实施更新，环境光源会改变此选项。

  --Backed 烘焙，环境光源不会改变选择此项。

#### 反射光照

- 根据天空盒或立方体贴图计算的作用于所有物体的反射效果，通过Environment Lighting 中Reflection 控制。

- Reflection Source 反射源

  --Skybox 天空盒

  Resolution 分辨率 Compression 是否压缩

  --Custom 自定义

  Cubemap 立方体贴图

- Reflection Intensity 反射强度

- Reflection Bounces 使用 Reflection Probe 后允许不同游戏对象间来回反弹的次数。

#### 间接光照(反弹光)

- 物体表面在接受光照后反射出来的光。

- 通过Light组件中Bounce Intensity 反弹强度控制。

- 通过Scene面板Irradiance 模式查看间接光照。

- 注意：

  只有标记Lightmaping Static 的物体才能产生间接反弹光照。非常消耗性能。

### 实时GI(Realtime GI)

- 所谓“实时”是指在运行期间任意修改光源，而所有的变化可以立即更新。
- 正是由于Unity 5 引入了行业领先的实时全局光照技术 Enlighten系统，才可以在运行时产生间接光照，使场景更为真是丰富。开发中做了预计算，所以能实时改变光
- 操作步骤：
  1. 游戏对象设置为Lightmaping Static
  2. 启用Lighting 面板的Precomputed Realtime GI
  3. 点击Build按钮(如果勾选Auto 编辑器会自动检测场景的改动修复光照效果)

####  Precomputed Realtime GI

- Realtime Resolution：实时计算分辨率
- CPU Usage：CPU利用率，值越大实时渲染效率越高。

在手游里面基本不用实时GI。

### 烘焙GI

把光做成图片贴在物体上。

**烘焙 Lightmap**

- 当场景包含大量物体时，实施光照和阴影对游戏性能有很大影响。使用烘焙技术，可以将光线效果预渲染成贴图再作用到物体上模拟光影，从而提高性能。适用于在性能较低的设备上运行的程序。

#### 光源侦测 Light Probes

- 由于LightMapping只能作用于static物体，所以导致运动的物体与场景中的光线无法融合在一起，显得非常不真实。而Light Probes组件可以通过Probe收集光影信息，然后对运动物体邻近的几个Probe进行插值运算，最后将光照作用到物体上。

##### 步骤

1. 创建游戏对象Light Probe Group。
2. 添加侦测小球 Add Probe。
3. 点击Build按钮。(如果勾选Auto编辑器会自动检测场景的改动修复光照效果)。
4. 勾选需要侦测物体的MeshRender 组件的Use Light Probes 属性。

#### Baked GI

- Baked Resolution：烘焙光照贴图分辨率，建议比实时GI分辨率高10倍。
- BakedPadding：光照贴图中各形状间距，取值2到200.
- Compressed：是否压缩光照贴图，压缩则提高性能，缩小容量，但画质会降低。

#### General GI

- 常规GI设置，同时适用于实时GI与烘焙GI。

- Directional Mode 定向模式：

  -- Non —Directional 无定向模式，使用1种光照贴图存储光照信息。

  -- Directional 定向模式，使用2种光照贴图存储光照信息，相比之下效果更好，但空间占用更大。

  --Direction Specular 定向反射模式，使用4种光照贴图存储光照信息，效果最好，但占用空间最大。

- 除无定向模式外必须运行在GLES2.0与SM2.0以上的设备。GLES指OpenGL ES 针对移动端，从iPhone5s开始支持；SM指Shader Model针对PC端，目前大部分显卡支持。

- Indirect Intensity 最终间接光照、反射光照的强度。1为默认强度，小于1则减低强度，大于1则增大强度。

- Bounce Boost 增强间接光照。

- Default Parameters 高级GI参数。

  --Default 默认

  --Default — HighResolution 高分辨率

  --Default — LowResolution 低分辨率

  --Default — VeryLowResolution 非常低的分辨率

## 声音

- Unity支持的音频文件格式：

  MP3,ogg,wav,aif,mod,it,s3m,xm。

- 声音分为2D、3D两类

  3D声音：有空间感，近大远小。

  2D声音：适合背景音乐。

- 在场景中产生声音，主要依靠两个重要组件：

  Audio Listener 音频监听器：接受场景中音频源Audio Source发出的声音，通过计算机的扬声器播放声音。

  Audio Souce 音频源

### Audio Source

- 音频源：

  --Audio Clip音频剪辑：需要播放的音频资源。

  --Mute 静音：如果启用，播放音频没有声音。

  --Play On Awake 唤醒播放：勾选后场景启动时自动播放。

  --Loop 循环：循环播放音频。

  --Volume 音量：音量大小

  --Pitch 音调：通过改变音调值调节音频播放速度。1是正常播放。

  --Stereo Pan：2D声音设置左右声道。

  --Spatial Blend：2D与3D声音切换。









