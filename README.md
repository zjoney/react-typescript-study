# react-typescript-study

1. TypeScript工程化开发
TypeScript工程化开发 前端工程化就是通过流程规范化、标准化提升团队协作效率 通过组件化、模块化提升代码质量 使用构建工具、自动化工具提升开发效率 编译 => 打包(合并) => 压缩 => 代码检查 => 测试 => 持续集成

2. 初始化项目 
3. git规范和changelog
3.1 良好的git commit好处
可以加快code review 的流程
可以根据git commit 的元数据生成changelog
可以让其它开发者知道修改的原因
3.2 良好的commit
commitizen是一个格式化commit message的工具
validate-commit-msg 用于检查项目的 Commit message 是否符合格式
conventional-changelog-cli可以从git metadata生成变更日志

统一团队的git commit 标准

可以使用angular的git commit日志作为基本规范
提交的类型限制为 feat、fix、docs、style、refactor、perf、test、chore、revert等
提交信息分为两部分，标题(首字母不大写，末尾不要加标点)、主体内容(描述修改内容)
日志提交友好的类型选择提示 使用commitize工具
不符合要求格式的日志拒绝提交 的保障机制
需要使用validate-commit-msg工具
统一changelog文档信息生成
使用conventional-changelog-cli工具

4. 支持Typescript
tsconfig-json
编译选项
tsc --init
基本参数

参数	解释
target	用于指定编译之后的版本目标
module	生成的模块形式：none、commonjs、amd、system、umd、es6、es2015 或 esnext 只有 amd 和 system 能和 outFile 一起使用 target 为 es5 或更低时可用 es6 和 es2015
lib	编译时引入的 ES 功能库，包括：es5 、es6、es7、dom 等。如果未设置，则默认为： target 为 es5 时: ["dom", "es5", "scripthost"] target 为 es6 时: ["dom", "es6", "dom.iterable", "scripthost"]
allowJs	是否允许编译JS文件，默认是false，即不编译JS文件
checkJs	是否检查和报告JS文件中的错误，默认是false
jsx	指定jsx代码用于的开发环境 preserve指保留JSX语法,扩展名为.jsx,react-native是指保留jsx语法，扩展名js,react指会编译成ES5语法 详解
declaration	是否在编译的时候生成相应的.d.ts声明文件
declarationDir	生成的 .d.ts 文件存放路径,默认与 .ts 文件相同
declarationMap	是否为声明文件.d.ts生成map文件
sourceMap	编译时是否生成.map文件
outFile	是否将输出文件合并为一个文件，值是一个文件路径名，只有设置module的值为amd和system模块时才支持这个配置
outDir	指定输出文件夹
rootDir	编译文件的根目录，编译器会在根目录查找入口文件
composite	是否编译构建引用项目
removeComments	是否将编译后的文件中的注释删掉
noEmit	不生成编译文件
importHelpers	是否引入tslib里的辅助工具函数
downlevelIteration	当target为ES5或ES3时，为for-of、spread和destructuring中的迭代器提供完全支持
isolatedModules	指定是否将每个文件作为单独的模块，默认为true

严格检查

参数	解释
strict	是否启动所有类型检查
noImplicitAny	不允许默认any类型
strictNullChecks	当设为true时，null和undefined值不能赋值给非这两种类型的值
strictFunctionTypes	是否使用函数参数双向协变检查
strictBindCallApply	是否对bind、call和apply绑定的方法的参数的检测是严格检测的
strictPropertyInitialization	检查类的非undefined属性是否已经在构造函数里初始化
noImplicitThis	不允许this表达式的值为any类型的时候
alwaysStrict	指定始终以严格模式检查每个模块
额外检查

参数	解释
noUnusedLocals	检查是否有定义了但是没有使用的变量
noUnusedParameters	检查是否有在函数体中没有使用的参数
noImplicitReturns	检查函数是否有返回值
noFallthroughCasesInSwitch	检查switch中是否有case没有使用break跳出
模块解析检查

参数	解释
moduleResolution	选择模块解析策略，有node和classic两种类型,详细说明
baseUrl	解析非相对模块名称的基本目录
paths	设置模块名到基于baseUrl的路径映射
rootDirs	可以指定一个路径列表，在构建时编译器会将这个路径列表中的路径中的内容都放到一个文件夹中
typeRoots	指定声明文件或文件夹的路径列表
types	用来指定需要包含的模块
allowSyntheticDefaultImports	允许从没有默认导出的模块中默认导入
esModuleInterop	为导入内容创建命名空间,实现CommonJS和ES模块之间的互相访问
preserveSymlinks	不把符号链接解析为其真实路径
sourcemap检查

参数	解释
sourceRoot	调试器应该找到TypeScript文件而不是源文件位置
mapRoot	调试器找到映射文件而非生成文件的位置，指定map文件的根路径
inlineSourceMap	指定是否将map文件的内容和js文件编译在一个同一个js文件中
inlineSources	是否进一步将.ts文件的内容也包含到输出文件中
试验选项

参数	解释
experimentalDecorators	是否启用实验性的装饰器特性
emitDecoratorMetadata	是否为装饰器提供元数据支持
试验选项

参数	解释
files	配置一个数组列表，里面包含指定文件的相对或绝对路径，编译器在编译的时候只会编译包含在files中列出的文件
include	include也可以指定要编译的路径列表，但是和files的区别在于，这里的路径可以是文件夹，也可以是文件
exclude	exclude表示要排除的、不编译的文件，他也可以指定一个列表
extends	extends可以通过指定一个其他的tsconfig.json文件路径，来继承这个配置文件里的配置
compileOnSave	在我们编辑了项目中文件保存的时候，编辑器会根据tsconfig.json的配置重新生成文件
references	一个对象数组,指定要引用的项目

5. 支持React

6. 代码规范
规范的代码可以促进团队合作
规范的代码可以降低维护成本
规范的代码有助于 code review(代码审查)
6.1 常见的代码规范文档
airbnb中文版
standard中文版
百度前端编码规范
styleguide
CSS编码规范

7. 单元测试
7.1 安装配置 #


8. 持续集成
Travis CI 提供的是持续集成服务（Continuous Integration，简称 CI）。它绑定 Github 上面的项目，只要有新的代码，就会自动抓取。然后，提供一个运行环境，执行测试，完成构建，还能部署到服务器
持续集成指的是只要代码有变更，就自动运行构建和测试，反馈运行结果。确保符合预期以后，再将新代码集成到主干
持续集成的好处在于，每次代码的小幅变更，就能看到运行结果，从而不断累积小的变更，而不是在开发周期结束时，一下子合并一大块代码