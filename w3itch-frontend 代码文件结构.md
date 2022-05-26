### w3itch-frontend代码文件结构

- pages
	- `_app.tsx`
		- 定义了全局每个页面的wrapper function
		- Context Providers
			- [[UseWalletProvider]]
				- walletconnect.org 配置
			- [[AuthenticationProvider]]
				- definition from `components/pages/authentication.tsx`
				- 用户登录状态，登录信息
			- [[SnackBarProvider]]
			- SEO 配置