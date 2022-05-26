- [Next.js Documentation](https://nextjs.org/docs)
- Getting Started
	- 用npx创建项目
		-
		  ``` bash
		  		  npx create-next-app@latest
		  ```
		- 创建typescript项目需要加上flag `--typescript`
		-
		  ``` bash
		  		  npx create-next-app@latest --typescript
		  ```
		- 运行development server
		-
		  ``` bash
		  		  yarn dev
		  ```
- Basic Features
	- 路由
		- `pages/index.tsx`是整个网页的入口
		- `pages/about.tsx` 可以通过网页`/about`访问。
	- 动态路由
		- 如果你创建了名为`pages/post/[id].tsx` 的文件，则可以访问`/post/1`,`/post/2`等等。
	- Pre-rendering
		- Static Generation
			- 编译时渲染HTML
			- 依赖外部数据
				- 页面内容依赖外部数据: `getStaticProps`
				- 页面路径依赖外部数据: `getStaticPaths`
		- Server Side Rendering
			- 发生请求时渲染HTML
			- 依赖外部数据
				- 页面内容依赖外部数据: `getServerSideProps({req,res})`
	- CSS 支持
		- 全局CSS
			- 在`pages/_app.tsx` 中import。
		- 组件CSS
			- 使用文件名`[name].module.css` 表示某个CSS Module
			- 直接在组件中import CSS Module
	- Layouts （如导航栏，页脚等）
		- 每个页面重复使用
			- 定义Layout组件
			- 在`pages/_app.tsx`中wrap。
		- 页面单独的Layout
			- 给页面组件Page定义`getLayout(page)`方法
	- Image Optimizations
		- 本地图片
			- 使用import引入图片
			- Image组件展示
		- 网络图片
			- Image组件展示，手动指定`width`, `height` 和可选的 `blurDataURL`
		- `priority`属性
			- 优先加载图片
		- `layout="fill"`
			- 图片自动填充布局（不指定width和height时使用）
	- Static File Serving
		- 静态文件放在`public` 文件夹下
		- 访问时使用地址`\public\{filename}`
	- Environment Variables
		- Next自动加载`.env.local`中的环境变量
		- 在浏览器中使用环境变量
			- 使用`NEXT_PUBLIC_` 前缀
- Routing
	- Link Between Pages
		- 使用Link组件
		- 可以使用URL Object
			- `{pathname, query}`
	- UseRouter
		- 获取Router对象
		-
		  ``` js
		  		  const router = useRouter();
		  ```
		- 获取query对象: `router.query`
	- Shallow Routing
		- 只改变URL不改变当前页面
		-
		  ``` js
		  		  router.push('/?counter=10', undefined, { shallow: true })
		  ```
- API Routes
	- `pages/api/api_name.ts`定义的api需要用地址`/api/api_name` 访问
- Deployment
	- Vercel
	- Self-Hosting
		- Node.js
			-
			  ``` bash
			  			  next build
			  			  next start
			  ```
- Advanced Features
	- Styled Components
		- 开启方式
			-
			  ``` js
			  			  // next.config.js
			  			  
			  			  module.exports = {
			  			    compiler: {
			  			      // ssr and displayName are configured by default
			  			      styledComponents: true,
			  			    },
			  			  }
			  ```
		-
		  ``` js
		  		  const Button = styled.div` -- your css --`
		  ```
		- 直接在JSX中使用 `<Button> Me </Button>`
	- `pages/_app.tsx`
		- 定义全局每个页面组件的wrapper function
	- `pages/_documents.tsx`
		- 定义了全局每个页面的document markup
		- 只在服务器端渲染
		- 为了正确渲染，必须在组件内使用`<Html>`, `<Head />`, `<Main />` and `<NextScript />`
	- Custom 404/500 Page
		- `pages/404.tsx`
	- Custom error page
		- `pages/_error.tsx`
		-
		-