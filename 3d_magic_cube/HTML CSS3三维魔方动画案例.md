HTML CSS3三维魔方动画案例

## 01-Dem

### 1. 项目创建

1. 开发工具： HBuilderX
2. 创建项目： 点击“文件”  => "新建"  => ”项目“ => "01-demo_3d_magic_cube.html" 

```html
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>Demo for 3d magic cube</title>
    <link rel="shortcut icon" href="img/favicon.ico">
	<style></style>
</head>
<body>
	<div class="box"></div>
</body>
</html>
```

### 2. 创建立方体

#### 2.1 HTML 创建立方体

```html
<!-- 立方体 -->
<div class="box"></div>
```

#### 2.2 创建立方体样式

```html
<style>
	.box {
        /* 宽度 */
		width: 210px;
        /* 高度 */
		height: 210px;
        /* 背景颜色 */
		background: red;
	}
</style>
```

#### 2.3 立方体居中

```css
body {
	display: flex;
	/* 垂直剧居 */
	justify-content:center;
	/* 水平居中 */
	align-items: center;
	/* 必须设置body高度 */
	height: 100vh;
}
```

### 3. 创建立方体六面

#### 3.1 HTML

```html
<!-- 立方体 -->
<div class="box">
	<!-- 正面 -->
	<ul class="front">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
		<li>6</li>
		<li>7</li>
		<li>8</li>
		<li>9</li>
	</ul>
	<!-- 背面 -->
	<ul class="back">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
		<li>6</li>
		<li>7</li>
		<li>8</li>
		<li>9</li>
	</ul>
	<!-- 左面 -->
	<ul class="left">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
		<li>6</li>
		<li>7</li>
		<li>8</li>
		<li>9</li>
	</ul>
	<!-- 右面 -->
	<ul class="right">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
		<li>6</li>
		<li>7</li>
		<li>8</li>
		<li>9</li>
	</ul>
	<!-- 顶面 -->
	<ul class="top">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
		<li>6</li>
		<li>7</li>
		<li>8</li>
		<li>9</li>
	</ul>
	<!-- 底面 -->
	<ul class="bottom">
		<li>1</li>
		<li>2</li>
		<li>3</li>
		<li>4</li>
		<li>5</li>
		<li>6</li>
		<li>7</li>
		<li>8</li>
		<li>9</li>
	</ul>
</div>
```

#### 3.2 设置六面样式

1. 删除立方体样式

   ```css
   .box {}
   ```

2. 给立方体六面设置宽高和背景颜色

   ```css
   ul {
   	width: 210px;
   	height: 210px;
   	background: red;
       /* 取消无序列表序号 */
       list-style: none;
   }
   ```

3. 给立方体数字设置样式

   ```css
   li {
   	/* 宽度 */
   	width: 60px;
   	/* 高度 */
   	height: 60px;
   	/* 背景颜色 */
   	background: #000;
   	/* 字体颜色 */
   	color: white;
   	/* 字体大小 */
   	font-size: 28px;
   }
   ```

4. 取消ul默认样式

   ```css
   ul {
       /* 取消无序列表默认样式 */
   	padding: 0;
   }
   ```

5. 调整li样式

   ```css
   li {
       /* 外边距 */
   	margin: 5px;
       /* 设置圆角 */
   	border-radius: 20px;
   	/* 文字水平居中 */
   	text-align: center;
   	/* 文字垂直居中 */
   	line-height: 60px;
   }
   ```

6. 调整ul内边距

   ```css
   ul {
       padding: 5px;
   }
   ```

7. 修改ul，li背景颜色，

   ```css
   ul {
       /* 背景颜色设置为透明 */
   	background: transparent;
   }
   ```

8. 设置li的六面颜色

   ```css
   .front li { background: red; }
   .back li { background: green; }
   .left li { background: blue; }
   .right li { background: purple; }
   .top li { background: yellow; }
   .bottom li { background: darkcyan; }
   ```

### 3.3 旋转六面使之成为立方体

1. 要移动六面，必须为六面设置绝对定位，父级元素设置相对定位： 子绝父相；

   ```css
   .box { position: relative; }
   ul { position: absolute; }
   ```

2. 设置3D变换，必须为立方体box设定三维变换样式

   ```css
   .box {
   	/* 相对定位 */
   	position: relative;
   	/* 3d样式变换 */
   	transform-style: preserve-3d;
   }
   ```

3. 转换六面角度，使之成为立方体

   ```css
   /* 旋转六面成立方体 */
   .front { transform: translateZ(120px); }
   .back { transform: translateZ(-120px); }
   .left { transform: rotateY(-90deg) translateZ(120px); }
   .right { transform: rotateY(90deg) translateZ(120px); }
   .top { transform: rotateX(90deg) translateZ(120px); }
   .bottom { transform: rotateX(-90deg) translateZ(120px); }
   ```

4. 定义动画

   - 设置函数： @keyframes;
   - 定义动画名称： rotate

   ```css
   /* 定义动画 */
   @keyframes rotate {
   	0% { transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg); }
   	20% { transform: rotateY(30deg) rotateX(40deg) rotateZ(20deg); }
   	40% { transform: rotateY(-60deg) rotateX(-40deg) rotateZ(-20deg); }
   	60% { transform: rotateY(145deg) rotateX(80deg) rotateZ(10deg); }
   	80% { transform: rotateY(90deg) rotateX(60deg) rotateZ(-20deg); }
   	100% { transform: rotateY(135deg) rotateX(-45deg) rotateZ(30deg); }
    }
   ```

5. 调用动画

   ```css
   .box {
       /* 调用动画 */
   	animation: rotate 10s linear infinite alternate; 
   }
   ```

6. 设置3d三维视角

   ```css
   .box {
       /* 设置立方体的三维立体视角 */
   	perspective: 10000px;
   }
   ```

### 4. 完整代码

```html
<!DOCTYPE html>
<html lang="zh">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta http-equiv="X-UA-Compatible" content="ie=edge">
	<title>Demo of 3d magic cube</title>
	<link rel="shortcut icon" href="img/favicon.ico">
	<style>
		body {
			display: flex;
			/* 垂直剧居 */
			justify-content:center;
			/* 水平居中 */
			align-items: center;
			/* 必须设置body高度 */
			height: 100vh;
		}
		.box {
			/* 相对定位 */
			position: relative;
			/* 3d样式变换 */
			transform-style: preserve-3d;
			/* 设置立方体的三维立体视角 */
			perspective: 10000px;
			/* 调用动画 */
			animation: rotate 10s linear infinite alternate; 
		}
		ul {
			/* 取消无序列表序号 */
			list-style: none;
			width: 210px;
			height: 210px;
			/* 取消无序列表默认样式 */
			padding: 5px;
			/* 背景颜色设置为透明 */
			background: transparent;
			/* 绝对定位 */
			position: absolute;
		}
		li {
			/* 宽度 */
			width: 60px;
			/* 高度 */
			height: 60px;
			/* 字体颜色 */
			color: white;
			/* 字体大小 */
			font-size: 28px;
			/* 左浮动 */
			float: left;
			/* 外边距 */
			margin: 5px;
			/* 设置圆角 */
			border-radius: 20px;
			/* 文字水平居中 */
			text-align: center;
			/* 文字垂直居中 */
			line-height: 60px;
		}
		
		/* 旋转六面成立方体 */
		.front { transform: translateZ(120px); }
		.back { transform: translateZ(-120px); }
		.left { transform: rotateY(-90deg) translateZ(120px); }
		.right { transform: rotateY(90deg) translateZ(120px); }
		.top { transform: rotateX(90deg) translateZ(120px); }
		.bottom { transform: rotateX(-90deg) translateZ(120px); }
		
		/* 修改六面颜色 */
		.front li { background: red; }
		.back li { background: green; }
		.left li { background: blue; }
		.right li { background: purple; }
		.top li { background: yellow; }
		.bottom li { background: darkcyan; }
		
		/* 定义动画 */
		@keyframes rotate {
			0% { transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg); }
			20% { transform: rotateY(30deg) rotateX(40deg) rotateZ(20deg); }
			40% { transform: rotateY(-60deg) rotateX(-40deg) rotateZ(-20deg); }
			60% { transform: rotateY(145deg) rotateX(80deg) rotateZ(10deg); }
			80% { transform: rotateY(90deg) rotateX(60deg) rotateZ(-20deg); }
			100% { transform: rotateY(135deg) rotateX(-45deg) rotateZ(30deg); }
		 }
	</style>
</head>
<body>
	<!-- 立方体 -->
	<div class="box">
		<!-- 正面 -->
		<ul class="front">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
		</ul>
		<!-- 背面 -->
		<ul class="back">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
		</ul>
		<!-- 左面 -->
		<ul class="left">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
		</ul>
		<!-- 右面 -->
		<ul class="right">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
		</ul>
		<!-- 顶面 -->
		<ul class="top">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
		</ul>
		<!-- 底面 -->
		<ul class="bottom">
			<li>1</li>
			<li>2</li>
			<li>3</li>
			<li>4</li>
			<li>5</li>
			<li>6</li>
			<li>7</li>
			<li>8</li>
			<li>9</li>
		</ul>
	</div>
</body>
</html>
```

## 02-Demo采用外联样式实现3D动画效果

1. #### HTML

   - 项目名称： 02-demo_3d_magic_cube.html

![目录结构](https://s1.ax1x.com/2020/07/25/Ux67Ix.png) 

- 引入外部样式表

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8" />
		<title>demo 3d magic cube</title>
		<link rel="shortcut icon" href="img/favicon.ico">
     	<!-- 引入外部样式表 -->
		<link rel="stylesheet" href="css/index.css">
	</head>
	<body>
		<div class="box">
			<!-- 正面 -->
			<ul class="front">
				<li>1</li>
				<li>2</li>
				<li>3</li>
				<li>4</li>
				<li>5</li>
				<li>6</li>
				<li>7</li>
				<li>8</li>
				<li>9</li>
			</ul>
			<!-- 背面 -->
			<ul class="back">
				<li>1</li>
				<li>2</li>
				<li>3</li>
				<li>4</li>
				<li>5</li>
				<li>6</li>
				<li>7</li>
				<li>8</li>
				<li>9</li>
			</ul>
			<!-- 左面 -->
			<ul class="left">
				<li>1</li>
				<li>2</li>
				<li>3</li>
				<li>4</li>
				<li>5</li>
				<li>6</li>
				<li>7</li>
				<li>8</li>
				<li>9</li>
			</ul>
			<!-- 右面 -->
			<ul class="right">
				<li>1</li>
				<li>2</li>
				<li>3</li>
				<li>4</li>
				<li>5</li>
				<li>6</li>
				<li>7</li>
				<li>8</li>
				<li>9</li>
			</ul>
			<!-- 顶面 -->
			<ul class="top">
				<li>1</li>
				<li>2</li>
				<li>3</li>
				<li>4</li>
				<li>5</li>
				<li>6</li>
				<li>7</li>
				<li>8</li>
				<li>9</li>
			</ul>
			<!-- 底面 -->
			<ul class="bottom">
				<li>1</li>
				<li>2</li>
				<li>3</li>
				<li>4</li>
				<li>5</li>
				<li>6</li>
				<li>7</li>
				<li>8</li>
				<li>9</li>
			</ul>
		</div>
	</body>
</html>
```

1. #### CSS

   - index.css

   ```css
   body {
   	display: flex;
   	/* 垂直剧居 */
   	justify-content:center;
   	/* 水平居中 */
   	align-items: center;
   	/* 必须设置body高度 */
   	height: 100vh;
   }
   .box {
   	/* 相对定位 */
   	position: relative;
   	/* 3d样式变换 */
   	transform-style: preserve-3d;
   	/* 设置立方体的三维立体视角 */
   	perspective: 10000px;
   	/* 调用动画 */
   	animation: rotate 10s linear infinite alternate; 
   }
   ul {
   	/* 取消无序列表序号 */
   	list-style: none;
   	width: 210px;
   	height: 210px;
   	/* 取消无序列表默认样式 */
   	padding: 5px;
   	/* 背景颜色设置为透明 */
   	background: transparent;
   	/* 绝对定位 */
   	position: absolute;
   }
   li {
   	/* 宽度 */
   	width: 60px;
   	/* 高度 */
   	height: 60px;
   	/* 字体颜色 */
   	color: white;
   	/* 字体大小 */
   	font-size: 28px;
   	/* 左浮动 */
   	float: left;
   	/* 外边距 */
   	margin: 5px;
   	/* 设置圆角 */
   	border-radius: 20px;
   	/* 文字水平居中 */
   	text-align: center;
   	/* 文字垂直居中 */
   	line-height: 60px;
   }
   
   /* 旋转六面成立方体 */
   .front { transform: translateZ(120px); }
   .back { transform: translateZ(-120px); }
   .left { transform: rotateY(-90deg) translateZ(120px); }
   .right { transform: rotateY(90deg) translateZ(120px); }
   .top { transform: rotateX(90deg) translateZ(120px); }
   .bottom { transform: rotateX(-90deg) translateZ(120px); }
   
   /* 修改六面颜色 */
   .front li { background: red; }
   .back li { background: green; }
   .left li { background: blue; }
   .right li { background: purple; }
   .top li { background: yellow; }
   .bottom li { background: darkcyan; }
   
   /* 定义动画 */
   @keyframes rotate {
   	0% { transform: rotateY(0deg) rotateX(0deg) rotateZ(0deg); }
   	20% { transform: rotateY(30deg) rotateX(40deg) rotateZ(20deg); }
   	40% { transform: rotateY(-60deg) rotateX(-40deg) rotateZ(-20deg); }
   	60% { transform: rotateY(145deg) rotateX(80deg) rotateZ(10deg); }
   	80% { transform: rotateY(90deg) rotateX(60deg) rotateZ(-20deg); }
   	100% { transform: rotateY(135deg) rotateX(-45deg) rotateZ(30deg); }
    }
   ```

## 03-Vue_Demo

1. 项目名称： 03-demo_3d_magic_cube.html

![目录结构](https://s1.ax1x.com/2020/07/25/Uxcg0A.png)

1. #### 引入Vue插件

   - 方法一： 本地插件

     ```html
     <script src="js/vue.js"></script>
     ```

   - 方法二：DNS引入插件

     ```html
     <script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
     ```

2. #### 创建Vue 实例

   ```html
   <script>
   	const app = new Vue({
   		el: "#app",
   		data: {
   			list: ["front","back","left","right","top","bottom"]
   		}
   	})
   </script>
   ```

3. #### HTML代码

   ```html
   <div class="box" id="app">
   	<ul v-for="item in list" :class="item"><li v-for="item in 9" >{{item}}</li></ul>
   </div>
   ```

4. #### CSS样式

   与02-demo_3d_magic_cube.html相同

5. #### 全部代码

   ```html
   <!DOCTYPE html>
   <html>
   	<head>
   		<meta charset="utf-8" />
   		<title>demo 3d magic cube</title>
   		<link rel="shortcut icon" href="img/favicon.ico">
   		<link rel="stylesheet" href="css/index.css">
   		<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
   		<script src="js/vue.js"></script>
   	</head>
   	<body>
   		<div class="box" id="app">
   			<ul v-for="item in list" :class="item"><li v-for="item in 9" >{{item}}</li></ul>
   		</div>
   		<script>
   			const app = new Vue({
   				el: "#app",
   				data: {
   					list: ["front","back","left","right","top","bottom"]
   				}
   			})
   		</script>
   	</body>
   </html>
   ```

   

   