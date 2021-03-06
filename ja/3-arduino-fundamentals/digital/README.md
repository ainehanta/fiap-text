## デジタル入出力

デジタル入出力はArduinoを使う上で最も基本的な操作です．入力はピンへの電圧でHIGHかLOWを判断します．出力は任意のピンへHIGH(電源電圧)かLOW(0V)を出力できます．

### デジタル出力

Arduinoから任意のピンへデジタル出力をします．最初にデジタル出力として使うピンを出力モードにする必要があります．ちなみにアナログピン(A0~A5)もデジタル出力ピンとして使えます．状態によって変更する必要がないのであれば`setup`関数で設定することをおすすめします．
```C++
pinMode(13, OUTPUT); // pin13を出力にする
pinMode(A0, OUTPUT); // pinA0を出力にする
```

あとは出力を行うだけです．入力モードのピンに対して出力を行うと意味が変わるので注意しましょう．
```C++
digitalWrite(13, HIGH); // pin13から5Vが出力される
digitalWrite(13, LOW);  // pin13から0Vが出力される
```

### デジタル入力

ボタンを押した等のデジタル入力を行います．ピンに5V付近の電圧が入力されていれば`HIGH`，0V付近の電圧が入力されていれば`LOW`が取得できます．まずは例のごとく入力モードに設定しましょう．
```C++
pinMode(13, INPUT);
```

あとは入力値を取得しましょう．
```C++
uint8_t ret;
ret = digitalRead(13);
```

ボタンなどプルアップが必要なデバイスを読み込む場合，内臓のプルアップ抵抗を利用することができます．たかが抵抗Ⅰ本ですが外付け部品を減らせます．プルアップしたいピンのモードを`INPUT_PULLUP`にするだけです．
```C++
pinMode(13, INPUT_PULLUP);
digitalRead(13);
```
