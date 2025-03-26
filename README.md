# 毕设《基于Unity3D的虚拟校园漫游系统设计与实现-以南宁师范大学武鸣校区二期为例》
基于Unity3D的校园虚拟漫游，选取南宁师范大学武鸣校区二期部分，构建部分三维模型，实现了较为逼真的和交互良好的漫游系统。

以下是毕业论文部分节选。



## 目录

1 绪论 ................................................................... 1  
1.1 研究背景和意义.................................................... 1  
1.2 国内外研究现状.................................................... 1  
1.2.1 国外研究现状 ................................................ 1  
1.2.2 国内研究现状 ................................................ 2  
1.3 本文研究内容...................................................... 3  
1.4 本文章节安排...................................................... 3  
2 相关开发工具和技术介绍 ................................................. 4  
2.1 Unity3D ........................................................... 4  
2.2 Visual Studio ..................................................... 4  
2.3 三维建模技术...................................................... 4  
2.4 C#技术............................................................ 5  
2.5 MySQL 数据库 ...................................................... 5  
3 系统需求分析 ........................................................... 7  
[4 虚拟校园漫游系统设计 ................................................... 8](#4)  
[4.1 系统架构.......................................................... 8](#4.1)  
[4.2 系统整体设计...................................................... 8](#4.2)  
4.3 虚拟校园 3D 建模设计............................................... 9  
4.3.1 建模素材收集 ............................................... 10  
4.3.2 3D 建模思路与设计........................................... 10  
4.4 Unity3D 虚拟漫游系统功能设计 ..................................... 11  
4.4.1 界面设计 ................................................... 11  
4.4.2 管理员登录设计 ............................................. 12  
4.4.3 背景音乐设计 ............................................... 12  
4.4.4 漫游人称视角设计 ........................................... 12  
4.4.5 人物移动设计................................................ 12  
4.4.6 动态信息交互设计 ........................................... 12  
4.4.7 学校文化媒体播放设计 ....................................... 13  
4.4.8 校园自动寻路设计 ........................................... 13  
4.4.9 切换天空设计 ............................................... 13  
4.4.10 碰撞体检测设计 ............................................ 13  
4.4.11 风吹植被设计 .............................................. 14  
4.5 数据库设计....................................................... 14  
5 虚拟校园漫游系统实现 .................................................. 15  
5.1 软硬件平台....................................................... 15  
5.2 场景搭建和场景优化............................................... 15  
[5.2.1 建立 3D 模型 ................................................ 15](#5.2.1)  
5.2.2 添加材质纹理 ............................................... 20  
5.2.3 模型导出 ................................................... 21   
5.3 虚拟漫游交互实现................................................. 21  
5.3.1 界面实现 ................................................... 22  
5.3.2 管理员登录实现 ............................................. 24  
5.3.3 背景音乐实现 ............................................... 24  
5.3.4 第一人称漫游和第三人称漫游实现 ............................. 25  
5.3.5 人物移动、奔跑、跳跃 ....................................... 26  
5.3.6 动态信息交互实现 ........................................... 27  
5.4.7 学校文化媒体播放实现 ....................................... 30  
5.4.8 校园自动寻路导航实现 ....................................... 31  
5.4.9 切换天空实现 ............................................... 32  
5.4.10 碰撞体检测 ................................................ 33  
5.4.11 风吹植被实现 .............................................. 34  
5.4.12 开门交互实现 .............................................. 35  
5.5 系统发布......................................................... 36  
6 系统测试 .............................................................. 37  
6.1 性能测试......................................................... 37  
6.2 漫游交互手动测试................................................. 38  
6.3 测试总结......................................................... 38  
7 总结和展望 ............................................................ 40  
<a id="4"></a> 
## 4.虚拟校园漫游系统设计
&emsp;&emsp;本虚拟校园漫游系统采用 Unity3D 作为主要开发平台，利用其强大的 3D 图形渲染
能力和友好的用户交互界面，提供了一个逼真且交互性强的虚拟环境。
<a  id="4.1"></a>
### 4.1 系统架构
&emsp;&emsp;三维模型和资源层，负责构建和管理校园的三维视觉内容，包括建筑、植被、以及
地形建设，为用户提供了一个详尽且逼真的虚拟环境。用户界面层，提供菜单界面、管
理员登录界面、信息展示界面以及虚拟漫游界面，直接与用户交互，允许用户通过这些
界面访问系统的各种功能，如浏览活动信息、进行虚拟漫游等。业务逻辑层，包含角色
系统、UI 模块、背景音乐、特效模块以及数据表格。处理所有后台逻辑，如角色动作控
制、信息交互响应、音乐和特效的管理，以及活动信息的展示，确保用户操作的有效响
应和系统的流畅运行。数据层，通过 MySQL 数据库管理所有系统数据，支持底层的数据
存储和访问，包括用户数据、地点活动信息等，为业务逻辑层提供必要的数据支持。系
统架构如图 1 所示。

<p align="center">
  <img src="https://github.com/miku116/Design-and-implementation-of-virtual-campus-roaming-system-based-on-Unity3D/blob/main/IMG/%E7%B3%BB%E7%BB%9F%E6%9E%B6%E6%9E%8403.png" 
       width="525" 
       height="300"
       alt="图1"
       style="border: 1px solid #e1e4e8; border-radius: 6px;">
  <br>
  <sub>图1 系统架构图</sup>
</p>
<a id="4.2"></a>

### 4.2 系统整体设计
&emsp;&emsp;以校园中的教学楼和其他关键建筑为核心，通过使用 Blender 进行 3D 建模，不再现了建筑物的外观，还规划了具体布局，以支持深入的虚拟漫游体验。同时，为了增强用户体验，系统采用了直观的交互设计，允许用户通过简单的点击和视野切换来探索虚拟环境，访问建筑详细信息，进行场景切换，以及利用导航工具进行自动寻路，使漫游变得更为直接和个性化，系统整体设计如图 2 所示。
<p align="center">
  <img src="https://github.com/miku116/Design-and-implementation-of-virtual-campus-roaming-system-based-on-Unity3D/blob/main/IMG/%E7%B3%BB%E7%BB%9F%E6%95%B4%E4%BD%93%E8%AE%BE%E8%AE%A102.png" 
       width="525" 
       height="300"
       alt="图2"
       style="border: 1px solid #e1e4e8; border-radius: 6px;">
  <br>
  <sub>图2  系统整体设计图</sup>
</p>

<a id="5.2.1"></a>
#### 5.2.1 建立3D模型
&emsp;&emsp;虚拟校园漫游系统的实体对象包含学校教学楼建模、体育场建模、教室建模、体育
馆建模、植被树木建模等。利用 Blender 这个强大的建模工具，根据收集的卫星图和现
场照片构建学校建筑的基本几何形状，这包括墙面、屋顶、窗户以及其他主要结构。过
程中经过仔细观察，校园里的建筑结构据有一定的对称性和规律性，如，立柱、窗户、
门等都是可以用 Blender 中的镜像、排列、实体化等修改器和几何节点进行复制，排列，
翻转等操作，可以使整个建模过程更为简洁，快速。
&emsp;&emsp;（1）教学楼建模：对教学楼进行模型的搭建，更具实际和收集来的图片，选用多边
形建模方法。在 Blender 软件中创建多边形立方体，根据具体实际的建筑结构建出基础
建筑角来拓展整体模型，然后对模型进行加工，进行环切、挤出和内插，教学楼的形态
就基本形成，再对其细加工，完善教学楼的各个不同的面。教学楼 3D 模型如图 6、7 所
示。
<p align="center">
  <img src="https://github.com/miku116/Design-and-implementation-of-virtual-campus-roaming-system-based-on-Unity3D/blob/main/IMG/%E6%AD%A62%E6%95%99%E5%AD%A6%E6%A5%BC02.png" 
       width="525" 
       height="300"
       alt="图2"
       style="border: 1px solid #e1e4e8; border-radius: 6px;">
  <br>
  <sub>图6  Blender 中教学楼正面建模</sup>
</p>
<p align="center">
  <img src="https://github.com/miku116/Design-and-implementation-of-virtual-campus-roaming-system-based-on-Unity3D/blob/main/IMG/%E6%AD%A62%E6%95%99%E5%AD%A6%E6%A5%BC.png" 
       width="525" 
       height="300"
       alt="图2"
       style="border: 1px solid #e1e4e8; border-radius: 6px;">
  <br>
  <sub>图7  Blender 中教学楼侧面建模</sup>
</p>