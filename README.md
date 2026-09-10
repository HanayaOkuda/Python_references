# Python sample codes
最終更新 2019/05/10

## 内容
内容の詳細は[wiki](https://github.com/HanayaOkuda/Python_references/wiki)をみてね。


* "[Python](https://github.com/HanayaOkuda/Python_references/wiki/1.-basic), [matplotlib](https://github.com/HanayaOkuda/Python_references/wiki/2.-matplotlib)" 
* "[Data read and write](https://github.com/HanayaOkuda/Python_references/wiki/3.-Data-read-and-write)"
* "[NumPy](https://github.com/HanayaOkuda/Python_references/wiki/4.-NumPy)" 
* "[Cython](https://github.com/HanayaOkuda/Python_references/X.-Cython)" 
* "[Pandas](https://github.com/HanayaOkuda/Python_references/Y.-Pandas)"
* "[SciPy](https://github.com/HanayaOkuda/Python_references/wiki/Z.-SciPy)"

## 推奨環境
Python 3.x をベースにします(Python 2.x は別言語なので注意)。

実行環境はJupyter Notebookが使いやすいです(Anaconda3にデフォルトで入ってます)。

NumPyとかmatplotlibとか使いたいと思うんですが、Anaconda3を入れれば全部入ってきます。

「Anaconda3なんか使いたくない!」っていう人は頑張ってNumPyとか入れてください。

とりあえずAnaconda3を入れておくことを推奨します(https://www.anaconda.com/distribution/ )。自分のOSに合わせてインストールしてください。その時にPython 2.x を選ばないように注意。

あとはCythonを使いたい人がいる場合、Visual Studioを入れろと言われることがあります。その場合は先にAnaconda3を入れているとCのライブラリと紐づけがうまくいかないので、一度Anaconda3をアンインストールして、Visual Studioをダウンロードし、その際にAnaconda3をVisual Studio経由で入れるとうまくいきます。

## Windows上のWSL2に入れたAnaconda3で仮想環境をビルドしてjupyter lab上で選択できるようにするメモ

"wsl上で" conda create -n <NAME> python=3.10 する。このときpythonのバージョンを指定する
Anaconda prompt上だとwsl環境の外のwindowsの上にビルドされたanacondaの環境に仮想環境を作ってしまう

conda activate <NAME>
conda install jupyter ipykernel <-- PATHが通らなくてうまくいかない場合はここのipykernelは一回uninstallしてもう一回installしなおしたらうまくいったりする？
ipython kernel install --user --name=<NAME> --display_name=<NAME> 
/home/<USER>/anaconda3/envs/<NAME>/share/jupyter/kernels/python3 の下にあるkernel.json の中をみて、一番上のpythonへのパスがあってるか確認


たぶんここまででJupyter lab上ではkernelが見えてて選択できるはずなので、新しくnotebookを作って(既存ファイルでkernelを変えて試すとキャッシュか何かでうまく読めないことがあった)、
import sys
print(sys.path)
print(sys.executable)
print(sys.version)をやって、選んだpythonのバージョンが選択されてるかを確認。この時、うまく仮想環境のpythonのバージョンが選択されてないケースがある(PATHが通ってない？)
その場合、"~/.bashrc"の最終行に、"export PATH=/home/<USER>/anaconda3/envs/<NAME>/bin:$PATH" を追加 (conda info -e でpathが見えるはず)

source ~/.bashrc するか、bash_profileの一番下にsource ~\.bashrcを書いておくことで起動時に自動でsourceさせる(<--あってる？)
