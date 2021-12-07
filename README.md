# spring-boot-cnbp-demo
SpringBootアプリケーションでCloudNativeBuildpacksのビルド時に環境変数を渡すデモ。

具体的には以下の部分でgradle taskに来た環境変数をbuildpackにプロキシしている。
https://github.com/miketako3/spring-boot-cnbp-demo/blob/d07d067ee7dd7a93aa53970e369204cf128e11f1/build.gradle#L27

環境変数の定義についてはbuildpackの定義を参照。

paketoの場合は [こちら](https://github.com/paketo-buildpacks/image-labels#behavior) 

## コマンド例

```shell
$ export BP_IMAGE_LABELS='hogehogetag=test'
$ ./gradlew bootBuildimage
$ docker inspect cnbp-demo:0.0.1-SNAPSHOT | jq '.[0].Config.Labels'
{
  ...
  "hogehogetag": "test",
  ...
}
```