# Levee failure by piping simulator (levee_sim) and window app — companion source for the book

Design documents and code for the levee failure simulator built in ***Toward a Million Lines XVI — Building a Levee Failure Simulator*** (Japanese title 『LLM で 100 万行のソフトウェア開発 XVI — 堤防崩壊のシミュレータをつくる』; the book is in Japanese).

`levee_sim` (Python) follows a levee that fails without being overtopped: when the water level rises, water passes through the soil layer under the levee and carries sand out at the landside toe, a pipe of removed sand grows toward the lake, and the levee loses its support, settles and breaches. The **ground** is a mixture fluid of soil and water (Darcy flow where the soil is packed, a viscous flow where it has yielded) and the **levee** is a set of bonded particles (discrete element method); the two are coupled in both directions. Two ground types are calculated: the **sand type** (the pipe grows from its tip and the levee collapses) and the **clay type** (a gap placed at the bottom of the levee is eroded and widens; **no pipe forms**). It writes figures and 2-D and 3-D animations. A Windows **window app** (Flutter) sets the parameters, starts the computation, shows progress and plays the animations. **The window holds no computation of its own**: every button runs a `levee_sim` command and reads the result files it writes. In this project **the design documents are the source of the code**. The results are results of a model, not forecasts, and not a reproduction of any real levee.

## Download

**The ready-to-run app and the source are on the [Releases](../../releases) page**, not in this repository. The release has four separate ZIPs:

| File | Contents |
|:---|:---|
| `levee_failure_exe.zip` | The Windows window app, ready built (**Japanese screens**), with the simulator it runs (Japanese display) and a small-example launcher |
| `levee_failure_exe_en.zip` | The same app (**English screens** by default), with the English-display simulator (progress lines, figure and animation labels in English) |
| `levee_failure.zip` | Design documents (`docs/`, Japanese, L1-L4, the source; `docs_en/`, the complete set for English readers: L1-L3 translated into English, L4 the Japanese originals as is) in separate folders, the code (`src/levee_sim/` with Japanese display, `src_en/` with English display, `app/`), the requirements specification (30 requirements), and empty databases (`ledger/`) |
| `levee_failure_animations.zip` | The animations of the two calculations of the book, from the start to the breach (sand type and clay type): MP4 video files only (the text inside the videos is Japanese) |

The app needs Python 3.11 and numpy, scipy, numba, matplotlib and pillow on your PC (see the README inside the ZIPs); extract to a short path. There is **no APK** (the app is a Windows desktop app). The app is **not code-signed**, so Windows may warn you. Computation results and tests are not included. The first run takes a few minutes (numba compiles); the base calculations of the book take several hours of real time, so try the bundled small example first and run large calculations on a machine with many cores.

You are free to change the design documents and the code and compare the results.

---

## License

- **The author holds the copyright.**
- **The code is under the GNU General Public License v3.0 or later (GPL-3.0-or-later).** The full text is [`LICENSE`](LICENSE). **If you modify it and distribute it, you must publish the source under the same GPL-3.0-or-later terms.**
- **The design documents and the text are under the Creative Commons Attribution-ShareAlike 4.0 International license (CC BY-SA 4.0).** This covers `docs/`, `docs_en/`, the READMEs and the other written text of this repository, and the text of the matching book. See [`LICENSE-DOCS.md`](LICENSE-DOCS.md).
- **If you use them, say so.** State where it came from (the title of the book and the name of this repository) and keep the copyright notice. If you changed it, say that you changed it.
- **In this project the design documents are the source of the code.** When you publish something made from this code, **publish the design documents together with the code.**
- Third-party components (numpy, scipy, numba, matplotlib and pillow installed by `pip`; the Flutter engine inside the EXEs) remain under their own original licenses.
- Provided "as is", without warranty — as the GPL-3.0 text says.

## 著作権とライセンス

- **著作権は、著者にあります。**
- **コードは、GNU General Public License v3.0 以降（GPL-3.0-or-later）です。**全文は [`LICENSE`](LICENSE) です。**改変して配布するときは、同じ GPL-3.0 以降の条件で、ソースを公開する義務があります。**
- **設計書と文章は、Creative Commons 表示-継承 4.0 国際（CC BY-SA 4.0）です。**このリポジトリの `docs/`・`docs_en/`・README ほかの文章と、対応する本の文章が当たります。内容は [`LICENSE-DOCS.md`](LICENSE-DOCS.md) です。
- **使ったときは、使ったことを書いてください。**どこから使ったか（本の題名と、このリポジトリの名前）と、著作権の表示を、使った先に書いてください。直したときは、直したことも書いてください。
- **このプロジェクトでは、設計書がコードの源です。**コードを使って作ったものを公開するときは、**設計書も、コードと一緒に公開してください。**
- 第三者の部品（`pip` で入る numpy・scipy・numba・matplotlib・pillow、EXE の中の Flutter の engine）は、それぞれの元のライセンスのままです。
- 現状のまま（as is）提供します。保証はありません（GPL-3.0 の全文のとおりです）。
