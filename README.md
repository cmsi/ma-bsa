# bsa - Baysian Scaling Analysis

## How to build bsa package

1. ソースファイルの準備 (ホスト上で)

        cd $HOME/vagrant/data/src
        wget https://github.com/KenjiHarada/BSA/archive/eb06870e0386f310621e3116b8c7a77c734e79a4.tar.gz -O - | tar zxf -
        mv BSA-eb06870e0386f310621e3116b8c7a77c734e79a4 bsa-20151218
        tar zcf bsa-20151218.tar.gz bsa-20151218
        rm -rf bsa-20151218

2. ビルドディレクトリの準備

        cd $HOME/build
        sh /development/ma-bsa/setup.sh

3. パッケージのビルド

        cd $HOME/build
        sh /development/ma-bsa/build.sh 2>&1 | tee build.log

4. パッケージへの署名

        cd $HOME/build
        debsign bsa_*.changes 

5. リポジトリへの登録

        cd $HOME/build
        sh /development/MateriAppsLive/repos/add_repo.sh bsa_*.changes
