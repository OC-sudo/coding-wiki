# Semantic Versioning 
(语义化版本 | セマンティックバージョニング)
## Summary
Given a version number MAJOR.MINOR.PATCH, increment the:

MAJOR version when you make incompatible API changes,
MINOR version when you add functionality in a backwards compatible manner, and
PATCH version when you make backwards compatible bug fixes.
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.
- - -
版本格式：主版本号.次版本号.修订号，版本号递增规则如下：

主版本号：当你做了不兼容的API 修改。
次版本号：当你做了向下兼容的功能性新增。
修订号：当你做了向下兼容的问题修正。
先行版本号及版本编译信息可以加到“主版本号.次版本号.修订号”的后面，作为延伸。
- - -
バージョンナンバーは、メジャー.マイナー.パッチ とし、バージョンを上げるには、

APIの変更に互換性のない場合はメジャーバージョンを、
後方互換性があり機能性を追加した場合はマイナーバージョンを、
後方互換性を伴うバグ修正をした場合はパッチバージョンを上げます。
　プレリリースやビルドナンバーなどのラベルに関しては、メジャー.マイナー.パッチ の形式を拡張する形で利用することができます。


- - -
## Introduction
- - -
In the world of software management there exists a dreaded place called “dependency hell.” The bigger your system grows and the more packages you integrate into your software, the more likely you are to find yourself, one day, in this pit of despair.

In systems with many dependencies, releasing new package versions can quickly become a nightmare. If the dependency specifications are too tight, you are in danger of version lock (the inability to upgrade a package without having to release new versions of every dependent package). If dependencies are specified too loosely, you will inevitably be bitten by version promiscuity (assuming compatibility with more future versions than is reasonable). Dependency hell is where you are when version lock and/or version promiscuity prevent you from easily and safely moving your project forward.

As a solution to this problem, I propose a simple set of rules and requirements that dictate how version numbers are assigned and incremented. These rules are based on but not necessarily limited to pre-existing widespread common practices in use in both closed and open-source software. For this system to work, you first need to declare a public API. This may consist of documentation or be enforced by the code itself. Regardless, it is important that this API be clear and precise. Once you identify your public API, you communicate changes to it with specific increments to your version number. Consider a version format of X.Y.Z (Major.Minor.Patch). Bug fixes not affecting the API increment the patch version, backwards compatible API additions/changes increment the minor version, and backwards incompatible API changes increment the major version.

I call this system “Semantic Versioning.” Under this scheme, version numbers and the way they change convey meaning about the underlying code and what has been modified from one version to the next.
- - -
在软件管理的领域里存在着被称作“依赖地狱”的死亡之谷，系统规模越大，加入的套件越多，你就越有可能在未来的某一天发现自己已深陷绝望之中。

在依赖高的系统中发布新版本套件可能很快会成为恶梦。如果依赖关系过高，可能面临版本控制被锁死的风险（必须对每一个相依套件改版才能完成某次升级）。而如果依赖关系过于松散，又将无法避免版本的混乱（假设兼容于未来的多个版本已超出了合理数量）。当你专案的进展因为版本相依被锁死或版本混乱变得不够简便和可靠，就意味着你正处于依赖地狱之中。

作为这个问题的解决方案之一，我提议用一组简单的规则及条件来约束版本号的配置和增长。这些规则是根据（但不局限于）已经被各种封闭、开放源码软件所广泛使用的惯例所设计。为了让这套理论运作，你必须先有定义好的公共API。这可以透过文件定义或代码强制要求来实现。无论如何，这套API 的清楚明了是十分重要的。一旦你定义了公共API，你就可以透过修改相应的版本号来向大家说明你的修改。考虑使用这样的版本号格式：XYZ （主版本号.次版本号.修订号）修复问题但不影响API 时，递增修订号；API 保持向下兼容的新增及修改时，递增次版本号；进行不向下兼容的修改时，递增主版本号。

我称这套系统为“语义化的版本控制”，在这套约定下，版本号及其更新方式包含了相邻版本间的底层代码和修改内容的信息。
- - -
　ソフトウェア・マネージメントの世界には、「依存性地獄」と呼ばれる恐ろしいものがあります。あなたのシステムが大きく成長すればするほど、さまざまなパッケージを組み込めば組み込むほど、自分が地獄の底にいることにいつか気づくでしょう。

　多くの依存性を有しているシステムにとって、新しいバージョンがリリースされることは悪夢でしかありません。厳密に依存関係を指定してしまうと、システムはバージョン・ロック（すべての依存パッケージを新しくしない限り、アップグレードできないこと）の危機にさらされてしまいます。反対に、依存指定を緩く管理しすぎると、バージョンが複雑に絡まり合い、痛い目にあうことは避けられないでしょう（合理性よりも将来のバージョンとの互換性を気にすることになる）。依存性地獄とは、あなたのプロジェクトでバージョン・ロックまたはバージョン混乱に陥ることで、プロジェクトに支障をきたすことを指します。

　この問題の解決策として、私はシンプルなルールセットとバージョン・ナンバーをどのように割り当て、バージョンを上げていくのかについての要件を提案します。これらのルールは既存のクローズドまたはオープンソースプロジェクトで普及している一般的な（必ずしもそうであるとは限りませんが）プラクティスをもとに作られています。このシステムを利用するために、まずはパブリックなAPIを宣言する必要があります。これはドキュメントに記載しても、コード自体で表現しても構いません。とにかく、APIが明確かつ正確であることは非常に重要です。パブリックなAPIを宣言したら、それを変更する際にはルールに従ってバージョン番号を上げなければなりません。つまり、X.Y.Z（メジャー.マイナー.パッチ）のバージョン形式を遵守しなければなりません。APIに影響を及ぼさないバグ修正はパッチバージョンを、後方互換性を保ちつつAPIを変更・追加した場合はマイナーバージョンを、後方互換性のないAPIの変更はメジャーバージョンを上げます。

　私はこのシステムを『セマンティック バージョニング』と呼び、このスキームに従えば、あるバージョンのコードが次のバージョンへの変更された際に何が変更されたのかユーザーに伝えることができます。
- - -
## Semantic Versioning Specification (SemVer)

The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in RFC 2119.

1. Software using Semantic Versioning MUST declare a public API. This API could be declared in the code itself or exist strictly in documentation. However it is done, it SHOULD be precise and comprehensive.

2. A normal version number MUST take the form X.Y.Z where X, Y, and Z are non-negative integers, and MUST NOT contain leading zeroes. X is the major version, Y is the minor version, and Z is the patch version. Each element MUST increase numerically. For instance: 1.9.0 -> 1.10.0 -> 1.11.0.

3. Once a versioned package has been released, the contents of that version MUST NOT be modified. Any modifications MUST be released as a new version.

4. Major version zero (0.y.z) is for initial development. Anything MAY change at any time. The public API SHOULD NOT be considered stable.

5. Version 1.0.0 defines the public API. The way in which the version number is incremented after this release is dependent on this public API and how it changes.

6. Patch version Z (x.y.Z | x > 0) MUST be incremented if only backwards compatible bug fixes are introduced. A bug fix is defined as an internal change that fixes incorrect behavior.

7. Minor version Y (x.Y.z | x > 0) MUST be incremented if new, backwards compatible functionality is introduced to the public API. It MUST be incremented if any public API functionality is marked as deprecated. It MAY be incremented if substantial new functionality or improvements are introduced within the private code. It MAY include patch level changes. Patch version MUST be reset to 0 when minor version is incremented.

8. Major version X (X.y.z | X > 0) MUST be incremented if any backwards incompatible changes are introduced to the public API. It MAY also include minor and patch level changes. Patch and minor version MUST be reset to 0 when major version is incremented.

9. A pre-release version MAY be denoted by appending a hyphen and a series of dot separated identifiers immediately following the patch version. Identifiers MUST comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers MUST NOT be empty. Numeric identifiers MUST NOT include leading zeroes. Pre-release versions have a lower precedence than the associated normal version. A pre-release version indicates that the version is unstable and might not satisfy the intended compatibility requirements as denoted by its associated normal version. Examples: 1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92, 1.0.0-x-y-z.–.

10. Build metadata MAY be denoted by appending a plus sign and a series of dot separated identifiers immediately following the patch or pre-release version. Identifiers MUST comprise only ASCII alphanumerics and hyphens [0-9A-Za-z-]. Identifiers MUST NOT be empty. Build metadata MUST be ignored when determining version precedence. Thus two versions that differ only in the build metadata, have the same precedence. Examples: 1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85, 1.0.0+21AF26D3—-117B344092BD.

11. Precedence refers to how versions are compared to each other when ordered.
Precedence MUST be calculated by separating the version into major, minor, patch and pre-release identifiers in that order (Build metadata does not figure into precedence).
Precedence is determined by the first difference when comparing each of these identifiers from left to right as follows: Major, minor, and patch versions are always compared numerically.
Example: 1.0.0 < 2.0.0 < 2.1.0 < 2.1.1.
When major, minor, and patch are equal, a pre-release version has lower precedence than a normal version:
Example: 1.0.0-alpha < 1.0.0.
Precedence for two pre-release versions with the same major, minor, and patch version MUST be determined by comparing each dot separated identifier from left to right until a difference is found as follows:
Identifiers consisting of only digits are compared numerically.
Identifiers with letters or hyphens are compared lexically in ASCII sort order.
Numeric identifiers always have lower precedence than non-numeric identifiers.
A larger set of pre-release fields has a higher precedence than a smaller set, if all of the preceding identifiers are equal.
Example: 1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0.
- - -
以下关键词MUST、MUST NOT、REQUIRED、SHALL、SHALL NOT、SHOULD、SHOULD NOT、 RECOMMENDED、MAY、OPTIONAL 依照RFC 2119 的叙述解读。（译注：为了保持语句顺畅， 以下文件遇到的关键词将依照整句语义进行翻译，在此先不进行个别翻译。）

1. 使用语义化版本控制的软件“必须MUST”定义公共API。该API可以在代码中被定义或出现于严谨的文件内。无论何种形式都应该力求精确且完整。
2. 标准的版本号“必须MUST”采用XYZ的格式，​​ 其中X、Y和Z为非负的整数，且“禁止MUST NOT”在数字前方补零。X是主版本号、Y是次版本号、而Z为修订号。每个元素“必须MUST”以数值来递增。例如：1.9.1 -> 1.10.0 -> 1.11.0。
3. 标记版本号的软件发行后，“禁止MUST NOT”改变该版本软件的内容。任何修改都“必须MUST”以新版本发行。
4. 主版本号为零（0.yz）的软件处于开发初始阶段，一切都可能随时被改变。这样的公共API 不应该被视为稳定版。
5. 1.0.0 的版本号用于界定公共API 的形成。这一版本之后所有的版本号更新都基于公共API 及其修改内容。
6. 修订号Z（xyZ | x > 0）“必须MUST”在只做了向下兼容的修正时才递增。这里的修正指的是针对不正确结果而进行的内部修改。
7. 次版本号Y（xYz | x > 0）“必须MUST”在有向下兼容的新功能出现时递增。在任何公共API的功能被标记为弃用时也“必须MUST”递增。也“可以MAY”在内部程序有大量新功能或改进被加入时递增，其中“可以MAY”包括修订级别的改变。每当次版本号递增时，修订号“必须MUST”归零。
8. 主版本号X（Xyz | X > 0）“必须MUST”在有任何不兼容的修改被加入公共API时递增。其中“可以MAY”包括次版本号及修订级别的改变。每当主版本号递增时，次版本号和修订号“必须MUST”归零。
9. 先行版本号“可以MAY”被标注在修订版之后，先加上一个连接号再加上一连串以句点分隔的标识符号来修饰。标识符号“必须MUST”由ASCII码的英数字和连接号[0-9A-Za-z-]组成，且“禁止MUST NOT”留白。数字型的标识符号“禁止MUST NOT”在前方补零。先行版的优先级低于相关联的标准版本。被标上先行版本号则表示这个版本并非稳定而且可能无法达到兼容的需求。范例：1.0​​.0-alpha、1.0.0-alpha.1、 1.0.0-0.3.7、1.0.0-x.7.z.92。
10. 版本编译信息“可以MAY”被标注在修订版或先行版本号之后，先加上一个加号再加上一连串以句点分隔的标识符号来修饰。标识符号“必须MUST”由ASCII的英数字和连接号[0-9A-Za-z-]组成，且“禁止MUST NOT”留白。当判断版本的优先层级时，版本编译信息“可SHOULD”被忽略。因此当两个版本只有在版本编译信息有差别时，属于相同的优先层级。范例：1.0.0-alpha+001、1.0.0+20130313144700、 1.0.0-beta+exp.sha.5114f85。
11. 版本的优先层级指的是不同版本在排序时如何比较。判断优先层级时，“必须MUST”把版本依序拆分为主版本号、次版本号、修订号及先行版本号后进行比较（版本编译信息不在这份比较的列表中）。由左到右依序比较每个标识符号，第一个差异值用来决定优先层级：主版本号、次版本号及修订号以数值比较，例如1.0.0 < 2.0.0 < 2.1.0 < 2.1.1。当主版本号、次版本号及修订号都相同时，改以优先层级比较低的先行版本号决定。例如：1.0.0-alpha < 1.0.0。有相同主版本号、次版本号及修订号的两个先行版本号，其优先层级“必须MUST”透过由左到右的每个被句点分隔的标识符号来比较，直到找到一个差异值后决定：只有数字的标识符号以数值高低比较，有字母或连接号时则逐字以ASCII的排序来比较。数字的标识符号比非数字的标识符号优先层级低。若开头的标识符号都相同时，栏 ​​位比较多的先行版本号优先层级比较高。范例：1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 10.0-beta.2 < 1.0.0-beta.11 < 1.0.0- rc.1 < 1.0.0。
- - -
この文書における各キーワード「しなければならない（MUST）」、「してはならない（MUST NOT）」、「要求されている（REQUIRED）」、「することになる（SHALL）」、「することはない（SHALL NOT）」、「する必要がある（SHOULD）」、「しないほうがよい（SHOULD NOT）」、「推奨される（RECOMMENDED）」、「してもよい（MAY）」、「選択できる（OPTIONAL）」は、RFC 2119に記載されている内容に従い解釈してください。

1. セマンティック バージョニングを適用するソフトウェアはパブリックAPIを宣言しなければなりません（MUST）。このAPIはコード自体で表現されているかもしれませんし、明確に文書として存在してるかもしれません。どちらにせよ、正確かつ漏れがないようにするべきです（SHOULD）。

2. 通常のバージョンナンバーは、X.Y.Zの形式にしなければなりません（MUST）。このときX、Y、Zは非負の整数であり（MUST）、各数値の先頭にゼロを配置してはなりません（MUST NOT）。Xはメジャーバージョン、Yはマイナーバージョン、Zはパッチバージョンを表します。各バージョンは数値的にバージョンアップしなければなりません（MUST）。例：1.9.0 -> 1.10.0 -> 1.11.0。

3. 一度パッケージをリリースしたのなら、そのバージョンのパッケージのコンテンツは修正してはなりません（MUST NOT）。いかなる修正も新しいバージョンとしてリリースしなければなりません（MUST）。

4. メジャーバージョンのゼロ（0.y.z）は初期段階の開発用です。いつでも、いかなる変更も起こりえます（MAY）。この時のパブリックAPIは安定していると考えるべきではありません（SHOULD NOT）。

5. バージョン1.0.0はパブリックAPIを定義します。このリリース後のバージョンナンバーの上げ方に関しては、パブリックAPIがどのくらい変更されるのかによって決まります。

6. パッチバージョン Z （x.y.Z | x > 0）は、後方互換性を保ったバグ修正を取り込んだ場合のみ、上げなければなりません（MUST）。バグ修正とは間違った振る舞いを修正する内部の変更のことを指します。

7. マイナーバージョン Y （x.Y.z | x > 0）は、後方互換性を保ちつつ機能性をパブリックAPIに追加した場合、上げなければなりません（MUST）。また、いかなるパブリックAPIも廃止予定としたのなら、上げなければなりません（MUST）。プライベートコード内での新しい機能の追加や改善を取り込んだ場合は、上げてもよいです（MAY）。その際にパッチレベルの変更も含めてもよいです（MAY）。マイナーバージョンを上げた際にはパッチバージョンを0にリセットしなければなりません（MUST）。

8. メジャーバージョン X （X.y.z | X > 0）は、パブリックAPIに対して後方互換性を持たない変更が取り込まれた場合、上げなければなりません（MUST）。その際にマイナーおよびパッチレベルの変更も含めてもよいです（MAY）。メジャーバージョンを上げた際には、パッチおよびマイナーバージョンを0にリセットしなければなりません（MUST）。

9. プレリリースバージョンは、パッチバージョンの直後にハイフンとドットで区切られた識別子を追加することで表現してもよいです（MAY）。識別子は必ずASCII英数字とハイフン [0-9A-Za-z-] でなければなりません（MUST）。識別子は空であってはなりません（MUST NOT）。数値の識別子はゼロから始めてはなりません（MUST NOT）。プレリリースバージョンは関連する通常のバージョンよりも低い優先度です。プレリリースバージョンは、不安定であり、関連する通常のバージョンが示す要件と互換性を満たさない可能性があります。例：1.0.0-alpha, 1.0.0-alpha.1, 1.0.0-0.3.7, 1.0.0-x.7.z.92。

10. ビルドメタデータはパッチまたはプレリリースバージョンの直後にプラス記号とドットで区切られた識別子を追加することで表現してもよいです（MAY）。識別子は必ずASCII英数字とハイフン [0-9A-Za-z-] でなければなりません（MUST）。識別子は空であってはなりません（MUST NOT）。バージョンの優先度を決める際にはビルドメタデータは無視されなければなりません（MUST）。つまり、2つのビルドメタデータだけが違うバージョンは、同じ優先度ということです。例：1.0.0-alpha+001, 1.0.0+20130313144700, 1.0.0-beta+exp.sha.5114f85。

11. バージョン同士をどのように比較するのかは優先度によって決まります。優先度はメジャー、マイナー、パッチ、プレリリース識別子の順番（ビルドメタデータは優先度に関して考慮しない）で分けて評価されなければなりません（MUST）。優先度は、各識別子を左から右に比較して最初の違いによって評価します。以下のように、メジャー、マイナー、パッチバージョンと常に数値的に比較します。例：1.0.0 < 2.0.0 < 2.1.0 < 2.1.1。メジャー、マイナー、パッチが同じ場合、プレリリースバージョンを持っている方が通常のバージョンよりも低い優先度です。例：1.0.0-alpha < 1.0.0。同じ、メジャー、マイナー、パッチを持つプレリリースバージョンの優先度の決定は、ドットで区切れた識別子を左から右に、異なるところが見つかるまで比較し決定しなければなりません（MUST）。数値のみで構成される識別子は数値的に比較され、文字列やハイフンを含む識別子はASCIIソート順に辞書的に比較されます。数値的な識別子は常に数値的でない識別子よりも低い優先度です。もし先行する識別子が同じ場合、プレリリースのフィールドが小さいセットよりも大きいセットのほうが高い優先度です。例：1.0.0-alpha < 1.0.0-alpha.1 < 1.0.0-alpha.beta < 1.0.0-beta < 1.0.0-beta.2 < 1.0.0-beta.11 < 1.0.0-rc.1 < 1.0.0。
- - -
## Backus–Naur Form Grammar for Valid SemVer Versions
```
<valid semver> ::= <version core>
                 | <version core> "-" <pre-release>
                 | <version core> "+" <build>
                 | <version core> "-" <pre-release> "+" <build>

<version core> ::= <major> "." <minor> "." <patch>

<major> ::= <numeric identifier>

<minor> ::= <numeric identifier>

<patch> ::= <numeric identifier>

<pre-release> ::= <dot-separated pre-release identifiers>

<dot-separated pre-release identifiers> ::= <pre-release identifier>
                                          | <pre-release identifier> "." <dot-separated pre-release identifiers>

<build> ::= <dot-separated build identifiers>

<dot-separated build identifiers> ::= <build identifier>
                                    | <build identifier> "." <dot-separated build identifiers>

<pre-release identifier> ::= <alphanumeric identifier>
                           | <numeric identifier>

<build identifier> ::= <alphanumeric identifier>
                     | <digits>

<alphanumeric identifier> ::= <non-digit>
                            | <non-digit> <identifier characters>
                            | <identifier characters> <non-digit>
                            | <identifier characters> <non-digit> <identifier characters>

<numeric identifier> ::= "0"
                       | <positive digit>
                       | <positive digit> <digits>

<identifier characters> ::= <identifier character>
                          | <identifier character> <identifier characters>

<identifier character> ::= <digit>
                         | <non-digit>

<non-digit> ::= <letter>
              | "-"

<digits> ::= <digit>
           | <digit> <digits>

<digit> ::= "0"
          | <positive digit>

<positive digit> ::= "1" | "2" | "3" | "4" | "5" | "6" | "7" | "8" | "9"

<letter> ::= "A" | "B" | "C" | "D" | "E" | "F" | "G" | "H" | "I" | "J"
           | "K" | "L" | "M" | "N" | "O" | "P" | "Q" | "R" | "S" | "T"
           | "U" | "V" | "W" | "X" | "Y" | "Z" | "a" | "b" | "c" | "d"
           | "e" | "f" | "g" | "h" | "i" | "j" | "k" | "l" | "m" | "n"
           | "o" | "p" | "q" | "r" | "s" | "t" | "u" | "v" | "w" | "x"
           | "y" | "z"

```
- - -
## Why Use Semantic Versioning?
This is not a new or revolutionary idea. In fact, you probably do something close to this already. The problem is that “close” isn’t good enough. Without compliance to some sort of formal specification, version numbers are essentially useless for dependency management. By giving a name and clear definition to the above ideas, it becomes easy to communicate your intentions to the users of your software. Once these intentions are clear, flexible (but not too flexible) dependency specifications can finally be made.

A simple example will demonstrate how Semantic Versioning can make dependency hell a thing of the past. Consider a library called “Firetruck.” It requires a Semantically Versioned package named “Ladder.” At the time that Firetruck is created, Ladder is at version 3.1.0. Since Firetruck uses some functionality that was first introduced in 3.1.0, you can safely specify the Ladder dependency as greater than or equal to 3.1.0 but less than 4.0.0. Now, when Ladder version 3.1.1 and 3.2.0 become available, you can release them to your package management system and know that they will be compatible with existing dependent software.

As a responsible developer you will, of course, want to verify that any package upgrades function as advertised. The real world is a messy place; there’s nothing we can do about that but be vigilant. What you can do is let Semantic Versioning provide you with a sane way to release and upgrade packages without having to roll new versions of dependent packages, saving you time and hassle.

If all of this sounds desirable, all you need to do to start using Semantic Versioning is to declare that you are doing so and then follow the rules. Link to this website from your README so others know the rules and can benefit from them.
- - -
这并不是一个新的或者革命性的想法。实际上，你可能已经在做一些近似的事情了。问题在于只是“近似”还不够。如果没有某个正式的规范可循，版本号对于依赖的管理并无实质意义。将上述的想法命名并给予清楚的定义，让你对软件使用者传达意向变得容易。一旦这些意向变得清楚，弹性（但又不会太弹性）的依赖规范就能达成。

举个简单的例子就可以展示语义化的版本控制如何让依赖地狱成为过去。假设有个名为“救火车”的函式库，它需要另一个名为“梯子”并已经有使用语义化版本控制的套件。当救火车创建时，梯子的版本号为3.1.0。因为救火车使用了一些版本3.1.0 所新增的功能， 你可以放心地指定相依于梯子的版本号大等于3.1.0 但小于4.0.0。这样，当梯子版本3.1.1 和3.2.0 发布时，你可以将直接它们纳入你的套件管理系统，因为它们能与原有相依的软件兼容。

作为一位负责任的开发者，你理当确保每次套件升级的运作与版本号的表述一致。现实世界是复杂的，我们除了提高警觉外能做的不多。你所能做的就是让语义化的版本控制为你提供一个健全的方式来发行以及升级套件，而无需推出新的相依套件，节省你的时间及烦恼。

如果你对此认同，希望立即开始使用语义化版本控制，你只需声明你的函式库正在使用它并遵循这些规则就可以了。请在你的README 文件中保留此页连结，让别人也知道这些规则并从中受益。

このアイデアは新しいものでもなければ、革新的なものでもありません。実際、みなさんも似たような取り組みを既におこなっているかもしれません。問題は「似ている」のでは不十分だということです。正式な仕様書による取り決めがなければ、バージョンナンバーは依存性の管理において基本的には無意味です。上記のアイデアに対して名前と正確な定義を与えることよって、あなたの開発するソフトウェアにおいて、あなたの意図がユーザーに対して伝わりやすくなることでしょう。一度、これらの意図を正確にしてしまえば、柔軟な（しかし、柔軟すぎてはいけない）依存性の仕様を作ることができます。

　単純な例として、セマンティック バージョニングがどのように依存性地獄を過去のものとするかについて説明します。「Firetruck」と呼ばれるライブラリについて考えてみましょう。それはセマンティック バージョニングされた「Ladder」というパッケージを必要とします。Firetruckを作成した時、Ladderはバージョン3.1.0でした。Firetruckは、バージョン3.1.0時に導入されたいくつかの機能を使用しているので、Ladderが3.1.0以上4.0.0未満の範囲で安全に依存性を指定できます。Ladderのバージョン3.1.1と3.2.0が利用可能になった時、それらをパッケージ管理に取り込んでリリースすることができ、それらが既存の依存するソフトウェアと互換性があるということは明確です。

　賢明な開発者であれば、もちろんパッケージがアップグレードされたのならその機能を使ってみたいと思うはずでしょう。ただ、現実は混沌としていて、我々ができることといったら、慎重になることくらいです。セマンティック バージョニングを実践することで、新しい依存パッケージを巻き込むことなく、まともな方法でリリース、アップグレードすることができ、手間と時間を節約してくれることでしょう。

　もし全面的に同意できると感じたのなら、セマンティック バージョニングを実践していることを宣言し、ルールを守って下さい。それからあなたのREADMEからこのWebサイトにリンクしてください、そうすれば、他の人がこのルールを知り、役立てることができるでしょう。
- - - 

# Naming conventions
(命名规范 | 命名規則)

说到命名规范，个人认为包含了目录，文件以及变量的命名。提前先说一句，命名规则没有谁对谁错，在项目中保持一致才是关键。

混乱或错误的命名不仅让我们对代码难以理解，更糟糕的是，会误导我们的思维，导致对代码的理解完全错误。相反，良好的命名，则可以让我们的代码非常容易读懂，也能向读者正确表达事物以及逻辑的本质，从而使得代码的可维护性就大大增强，读命名好的文章是非常流畅的，会有一种享受的感觉。

* 目录
由于Windows, OSX下文件名不区分大小写(linux是区分的)，所以命名我们建议还是以全部小写为主，个人习惯连字符使用-中划线。比如: my-project-name

项目中的子目录一般按照作用，使用常用单词表示，有复数的情况，使用复数命名法，比如: scripts, styles, images和data-modules

* 文件
文件的命名我个人也是推荐使用-中划线进行连接。和目录的连接字符保持一致。但是linux系统文件推荐的文件命名一般是下划线。

* 变量
变量命名有两种方式:

    * 下划线命名法: my_variable
    * 驼峰式命名法: myVariale
当然不同语言也是有不同的规范，网上也有很多大公司的命名规范可以参考。

* JavaScript
变量推荐驼峰式命名法

* CSS
推荐使用中划线进行连接，CSS 语法本身就使用连字号作为连接（比如 font-family，text-align等）

## Python Style Guide 
[Python Style Guide](PEP-8-style-guide-for-python-code.md)

# Writing Documentation
## github如何管理文档
讨论一下我们如何使用 Github Page 服务运行 Github 帮助文档 （目前每月有上百万的访问量）的。

### 以前的流程
用于托管维护网站、管理网站所用资源和文档搜索增强的 Rails 应用程序
用户托管由一大堆 Markdown 文件组成的网站具体内容
我们正常的撰写流程可能是这个样子的:

当有新特征开发出来的时候文档团队首先编写好文档内容
创建一个新的 issue 去追踪这个特征
当文档更新完毕一切就绪之后，我们会发起一个 pull request 去迭代更新文档内容。
PR 发起成功后，我们会使用 @ 方式提醒团队（比如 @github/docs ）并会让队友们审查一下我们的内容。
当这个特征开发完毕已经上线的时候，我们会合并之前创建的 PR。 使用 webhook 能够帮助我们在 内容仓库 快速激活我们部署的 Rails应用程序。webhook 承担了负责更新数据库的任务。

### 新的流程
当 Jekyll 2.0 发布的时候，我们看到了曙光，是时候该把我们这套该死的流程换成纯静态站了！特别是新增加的 Collections 文档类型能让你定义你需要的文件结构。另外，Jekyll 2.0 还增加了 Sass 和 CoffeeScript 的支持，这将使得编写前端代码变的更为简单便捷。

## markdown + git 最适合程序员的wiki系统
gollum 是github的使用的一个基于markdown的 wiki系统。 最重要的是gollum直接和git集成不需要数据库，你可以选择在Web页面撰写文档，也可以用你喜欢的markdown工具编辑文档在命令行进行提交。 “markdown+git = wiki” 这对程序员来讲绝对是最棒的选择。

_Mac下安装的适合遇到了一些小问题，所以在这里记录一下安装过程。_

* 基本的环境
在安装之前，假定我们已经拥有了mac 下的包管理工具 homebrew 及 ruby 运行环境。我当前的工作环境如下:
    1. Mac 10.9
    2. homebrew 0.9
    3. ruby 2.0
* 安装 Gollum
我们可以选择通过二进制或者源码的方式进行安装。

    * 二进制安装
在安装的时候会出现找不到libiconv所以需要安装下面的依赖库
    ```
    brew install libxml2 libxslt
    brew link libxml2 libxslt --force
    wget http://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.13.1.tar.gz
    tar xvfz libiconv-1.13.1.tar.gz
    cd libiconv-1.13.1
    ./configure --prefix=/usr/local/Cellar/libiconv/1.13.1
    make
    sudo make install
    ```
    * 通过Gem安装 gollum
    ```
    [sudo] gem install gollum
    ```
    * 源码安装
    ```
    git clone https://github.com/gollum/gollum
    cd gollum
    bundle install
    ```
    安装成功后尝试着在终端输入下面的命令，如果能够正常显示版本号则说明安装成功.
    ```
    gollum --v
    ```
* 创建自己的wiki系统
接下来我们就可以建立自己的wiki系统了，建立一个名字为”wiki”的目录使用git进行管理。进入到wiki目录，在wiki目录下启动gollum
```
mkdir wiki
cd wiki
git init
gollum
```
显示如下：
```
[2015-01-21 14:03:45] INFO  WEBrick 1.3.1
[2015-01-21 14:03:45] INFO  ruby 2.0.0 (2013-05-14) [x86_64-darwin12.4.1]
== Sinatra/1.4.5 has taken the stage on 4567 for development with backup from WEBrick
[2015-01-21 14:03:45] INFO  WEBrick::HTTPServer#start: pid=17699 port=4567
```
接下就可以在浏览器中访问了 http://localhost:4567/

创建wiki文档可以选择在全部Web界面进行操作，也可以选择在终端命令行进行提交管理markdown文件，在浏览器中进行查看。

# Open Source Protocol
开源协议
[Choose an open source license](https://choosealicense.com/)
## Open Source Protocol

> Open Source Protocol: Tell the world where your website lives.

### About

The Open Source Protocol is a way of telling developers where to access the source code for your website, if the source code is hosted in an open source repository on the public internet.

The OS Protocol uses metatags. To include an open source metatag on your website, simply add `<meta />` tags for the following properties:

*   `os:repo` - This should be a link to the repository web page, for instance the project page on GitHub, Bitbucket, or Sourceforge.
*   `os:rcs_type` - This should be the name of the revision control system used, for instance Git, Mercurial, Bazaar.
*   `os:src` - This is the repository url that can be used to obtain a copy of the source.

This is not a place to link to code that is described on your website; rather, this is for the code _for the actual website_. That way, if anyone reading your website sees an error - a spelling mistake, broken CSS, etc. - or something they want to examine - a cool paralax library, etc. - they can quickly fetch the source code.

The `os` protocol is loosely based on the [Open Graph protocol](http://ogp.me/), which in turn is based on [RDFa](https://en.wikipedia.org/wiki/RDFa). `os` stands for “open source”.

A `link` element must be added in order to adhere to the standard. This is similar to the now deprecated `profile` attribute, which used to go into the `<HEAD />`.

### Example

    <link rel="profile" href="http://osprotocol.com" />
    <meta property="os:repo" content="https://github.com/RichardLitt/open-source-protocol" />
    <meta property="os:rcs_type" content="git" />
    <meta property="os:src" content="git@github.com:RichardLitt/open-source-protocol.git" />
    

### Optional tags

Other tags that can be used:

*   `os:issue` - This links to a place to report issues for the website.
*   `os:commit` - This is the commit id that the current site is based upon, as that may not always be the same as HEAD.
*   `os:branch` - This is the branch where the live code for the website lives.
*   `os:server:*` - If there’s separate custom code for a server (for example, a server written using [node.js](https://nodejs.org/)), and the code for which doesn’t include the website content source as a submodule or mention it in some other way, then the tags `os:server:*` can be used to separately specify the server code. Here \* denotes all the other `os:*` tag subtypes specified in this document.

#### Examples

    <meta property="os:issue" content="https://github.com/RichardLitt/open-source-protocol/issues" />
    <meta property="os:commit" content="1sda73d" />
    <meta property="os:branch" content="gh-pages" />
    

### Shields

For use in the repository, to show your compliance and spread the word:

![passing](https://img.shields.io/badge/OSMT-passing-green.svg) [https://img.shields.io/badge/OSMT-passing-green.svg](https://img.shields.io/badge/OSMT-passing-green.svg)  
![failing](https://img.shields.io/badge/OSMT-failing-red.svg) [https://img.shields.io/badge/OSMT-failing-red.svg](https://img.shields.io/badge/OSMT-failing-red.svg)

### Participating Websites

This is a list of websites which have adopted this protocol. If you know of any others, please add them here.

*   [angular-meteor.com](http://angular-meteor.com/)
*   [burntfen.com](http://burntfen.com/)
*   [theuserismymom.com](http://theuserismymom.com/)

Projects building on OSP:

*   [OSMT-extension](https://github.com/RichardLitt/osmt-extension) Chrome extension to check for OSMT compliance. _WIP_.

### Contribute

This is a work in progress. Please open an [issue](https://github.com/RichardLitt/open-source-protocol/issues) to discuss how the Open Source Protocol can be improved. PRs are encouraged!

If you use the OSProtocol, please add your site above. Also, tell your friends.

To automatically copy `README.md` from `master` to `gh-pages`, use the hook on `gh-pages` in `dev`. (_Note: It doesn’t like `git add -p`_).

### Source

This project is maintained by [RichardLitt](https://github.com/RichardLitt).


[Source](https://osprotocol.com/)

# Index Structure
目录结构
不管大型还是小型项目，清晰的目录结构是开发过程的好的开始。以我常用的web项目为例，搭建一下目录结构.

## Overview
```
├── src
│   ├── js
│   │   ├── main.js
│   │   ├── plugins.js
│   │   └── vendor
│   │       └── modernizr-2.8.3.min.js
│   ├── css
│   │   └── main.css
│   ├── img
│   ├── favicon.ico
│   ├── humans.txt
│   ├── index.html
│   ├── 404.html
│   ├── apple-touch-icon.png
│   ├── browserconfig.xml
│   ├── crossdomain.xml
│   ├── robots.txt
│   ├── tile-wide.png
│   └── tile.png
├── test
│   ├── file_content.js
│   └── file_existence.js
├── dist
│   ├── 404.html
│   ├── LICENSE.txt
│   ├── apple-touch-icon.png
│   ├── browserconfig.xml
│   ├── crossdomain.xml
│   ├── css
│   │   ├── main.css
│   │   └── normalize.css
│   ├── favicon.ico
│   ├── humans.txt
│   ├── img
│   ├── index.html
│   ├── js
│   │   ├── main.js
│   │   ├── plugins.js
│   │   └── vendor
│   │       ├── jquery-1.11.2.min.js
│   │       └── modernizr-2.8.3.min.js
│   ├── robots.txt
│   ├── tile-wide.png
│   └── tile.png
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE.txt
├── README.md
├── gulpfile.js
├── package.json
```
目录结构清晰是首要目标，至于命名只要能达到表意的目的即可。

## src
此目录专注于开发，存放的都是源文件，不需要压缩合并。目录下主要分为：

* css(styles): 样式文件
* js(scripts): 脚本文件
* img(images): 图片素材
* font(fonts): 存放字体
* 其他: 按照分类不同划分目录

文件名上面，简写的话都使用单数形式，全称的话使用复数形式。

## dist
此目录为编译生成目录，用于部署环境，目录结构和src保持一致。

## test
此目录为测试目录，存放和项目测试相关的文件。

## doc
如果存在文档说明，放置在此目录下。

其他根目录文件
根目录下的其他文件，一般还有:

* .editorconfig: 代码样式统一格式文件
* .jscsrc:
* .travis.yml:
* .jshintrc: jshint配置文件
* csscomb.json: csscomb配置文件
* .gitignore: git忽略文件
* .gitattributes: git属性文件
* .bowerrc
* bower.json
* package.json
* gruntfile.js/gulpfile.js

# Regular Expressions
* [正则表达式入门](re-30min.md)