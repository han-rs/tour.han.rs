# 碎碎念

*这是一些碎碎念*. 你可以直接从正式章节开始学习.

建议先简单过一遍 [Rust 语言速查 (翻译中)](https://cheats.han.rs), 建立初印象.
看不懂没关系, 本指南会尽力给你掰碎了讲的.

## 为什么学 Rust?

- 如果你学的第一门编程语言就是 Rust, 那么恭喜你! 你将会有一个非常好的开始.

  作为现代编程语言, Rust 吸取了编程语言发展数十年来大量经验教训, 并将大量最优实践融入到了语言设计中.

  > 要学好 Rust, 你需要深入理解内存、堆栈、引用、变量作用域等这些其它高级语言往往不会深入接触的内容.
  > 另外, Rust 会通过语法、编译器和 `clippy` 这些静态检查工具半帮助半强迫的让你成为更优秀的程序员, 写出更好的代码.

  同时, 作为偏底层的语言, Rust 可以让你在有良好开发体验的同时帮助你更加了解操作系统、网络、性能优化等底层知识.
  搭配计算机组成原理, 操作系统原理等计算机系专业课程食用更佳.

  个人是强烈推荐将 Rust 作为第一门编程语言的 (笔者就是如此).

- 如果你已经熟练应用 C / C++, Rust 会让你感到非常亲切, 但又有很多不同之处, 需要仔细理解体会.

- 如果你是有 Java 基础的, 我的建议是抛弃掉一切 Java 编程经验, 从零开始学习 Rust, 否则会把很多坏习惯带过来.

- 如果你是 Go 开发者, 估计你会爱上 Rust 里面的错误处理范式. 不过, Go 作为另一门优秀的现代编程语言, 个人认为熟练掌握 Go 再来学 Rust 意义不大, 除非对性能有极致追求, 或者单纯开发工作要用到. 习惯了 Go 这种带 GC 的语言, Rust 的内存管理可能会让你有点不适应; 异步 Rust 可能会让你非常吃力.

- 如果你是 JavaScript / TypeScript / Python 等语言的开发者, 那也算是从 0 开始学习 Rust 了.

## 和编译器打交道?

编译器是每位初学者最好的老师之一.

## AI 赋能?

AI 很强大, 但写出来的东西你得知其所以然, 半桶水晃悠很容易被坑.

个人习惯把 AI 当文档库用.

## Rust 适合?

**Rust 在这些方面表现非常好**:

- Compiled code [about same performance](https://benchmarksgame-team.pages.debian.net/benchmarksgame/box-plot-summary-charts.html) as C / C++, and excellent [memory and energy efficiency](https://docente.ifsc.edu.br/mello/livros/java/paperSLE.pdf).

  和 C / C++ [接近的性能](https://benchmarksgame-team.pages.debian.net/benchmarksgame/box-plot-summary-charts.html), 优秀的[内存和能源效率](https://docente.ifsc.edu.br/mello/livros/java/paperSLE.pdf).
- Can [avoid 70% of all safety issues](https://www.chromium.org/Home/chromium-security/memory-safety) present in C / C++, and most memory issues.

  能避免 C / C++ 中存在的 [70% 的安全问题](https://www.chromium.org/Home/chromium-security/memory-safety), 以及大部分的内存安全问题.
- Strong type system prevents [data races](https://doc.rust-lang.org/nomicon/races.html), brings ['fearless concurrency'](https://blog.rust-lang.org/2015/04/10/Fearless-Concurrency.html) (amongst others).

  强类型系统阻止[数据竞争](https://doc.rust-lang.org/nomicon/races.html)、[无惧并发](https://blog.rust-lang.org/2015/04/10/Fearless-Concurrency.html) (等等).
- Seamless C interop, and [dozens of supported platforms](https://doc.rust-lang.org/rustc/platform-support.html) (based on LLVM).

  无缝的 C 互操作, 以及[大量支持的平台](https://doc.rust-lang.org/rustc/platform-support.html) (基于 LLVM).
- ["Most loved or admired language"](https://survey.stackoverflow.co/2023/#section-admired-and-desired-programming-scripting-and-markup-languages) for <strike>4</strike> <strike>5</strike> <strike>6</strike> <strike>7</strike> 8 years in a row. 🤷‍♀️

    连续 <strike>4</strike> <strike>5</strike> <strike>6</strike> <strike>7</strike> 8 年被评为 ["最受喜爱或令人钦佩的语言"](https://survey.stackoverflow.co/2023/#section-admired-and-desired-programming-scripting-and-markup-languages). 🤷‍♀️
- Modern tooling: `cargo` (builds _just work_), `clippy` (700+ code quality lints), `rustup` (easy toolchain mgmt).

  现代化的工具链: `cargo` (编译 _好简单_), `clippy` (700+ 代码质量检查点), `rustup` (便捷的工具链管理).

## Rust 不适合?

**你可能遇到的问题**:

- Steep learning curve;<sup>1</sup> compiler enforcing (esp. memory) rules that would be "best practices" elsewhere.

  陡峭的学习曲线;<sup>1</sup> 编译器强制执行在其他语言中可能只是 "最佳实践" 的 (特别是内存方面上的) 规则.
- Missing Rust-native libs in some domains, target platforms (esp. embedded), IDE features.<sup>1</sup>

  在某些领域、目标平台 (特别是嵌入式) 和 IDE 功能方面缺乏 Rust 原生库.<sup>1</sup>
- Longer compile times than "similar" code in other languages.<sup>1</sup>

  与其他语言写成的 "类似" 的代码相比, 编译时间更长.<sup>1</sup>
- Careless (use of `unsafe` in) libraries can secretly break safety guarantees.

  不谨慎 (使用 `unsafe` 的) 库可能会悄悄破坏安全保证.
- ~~No formal language specification~~, {{ link(url="https://spec.ferrocene.dev/") }} ~~can prevent legal use in some domains (aviation, medical, &hellip;)~~. {{ link(url="https://ferrous-systems.com/ferrocene/") }}

  ~~没有正式的语言规范~~ {{ link(url="https://spec.ferrocene.dev/") }} ~~可能会阻止在某些领域 (航空、医疗等) 的合法使用~~. {{ link(url="https://ferrous-systems.com/ferrocene/") }}
- Rust Foundation may offensively use their IP to affect _'Rust'_ projects (e.g, forbid names, impose policies). {{ link(url="https://devclass.com/2023/04/11/dont-call-it-rust-community-complains-about-draft-trademark-policy-restricting-use-of-word-marks/") }}{{ link(url="https://web.archive.org/web/20230413161930/https://old.reddit.com/r/rust/comments/12e7tdb/rust_trademark_policy_feedback_form/") }}<sup>2</sup>

  Rust 基金会可能会积极维护其知识产权, 影响到 _'Rust'_ 项目(例如, 禁止名称, 强制执行政策). {{ link(url="https://devclass.com/2023/04/11/dont-call-it-rust-community-complains-about-draft-trademark-policy-restricting-use-of-word-marks/") }}{{ link(url="https://web.archive.org/web/20230413161930/https://old.reddit.com/r/rust/comments/12e7tdb/rust_trademark_policy_feedback_form/") }}

<sup>1</sup> Compare [Rust Survey](https://blog.rust-lang.org/2020/04/17/Rust-survey-2019.html#why-not-use-rust). <br>
<sup>2</sup> Avoiding their marks (e.g, in your name, URL, logo, dress) is probably sufficient. 避免使用他们的商标 (例如在你的名称、URL、标志、外观中) 可能就足够了.
