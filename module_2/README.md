# 模組二：類別與控制結構

- 活動一：類別與物件

## 活動一：類別與物件

### 參考資源

[https://openhome.cc/zh-tw/java/object/](https://openhome.cc/zh-tw/java/object/)

![](../images/module_2_section1_outline.png)

### 程序知識

素材：

```java

class Clothes {
    String color;
    char size;
}

public class Field {
    public static void main(String[] args) {
        Clothes sun = new Clothes();
        Clothes spring = new Clothes();

        sun.color = "red";
        sun.size = 'S';        
        spring.color = "green";
        spring.size = 'M';
        
        System.out.printf("sun (%s, %c)%n", sun.color, sun.size);
        System.out.printf("spring (%s, %c)%n", spring.color, spring.size);
    }
}
```

- 定義 Clothes 類別，在 Clothes 類別中定義 2 個屬性
    - color 屬性，型態為 String
    - size 屬性，型態為 char
- 建立一個可執行的 Field 類別，執行後要印出目前有建立的 Clothes 物件。
    - sun 的 color 與 size 分別為 red 與 S
    - spring 的 color 與 size 分別為 green 與 M

### 概念知識

- 一份 Java 原始檔，可以被編譯成多個 `.class`
- `new` 是怎麼一回事呢？什麼是類別？什麼是物件？
- 使用 Reference Type 設定物件的屬性

### 事實知識

- 認識一些常見的類別
- 學習查詢 Javadoc



## 活動二：解說猜數字遊戲

在控制結構的部分，我們打算用「解說」猜數字遊戲的提示產生來進行。這裡的猜數字是指 `1A2B` 這種型式的猜數字，它的規則是猜測一組 4 位數的數字。其中數字不能重複。

舉例來說：

- 遊戲謎底為 `1234` 若玩家猜測為 `1234`，回應提示 `4A` 。
- 遊戲謎底為 `1234` 若玩家猜測為 `2134`，回應提示 `2A2B`。因為最後的 `34` 位置與謎底吻合，屬於數字與位置都猜對，判定為 `2A`。前面的 `21` 則只有數字對了，但位置不對，得 `2B`。
- 遊戲謎底為 `1234` 若玩家猜測為 `4567`，回應提示 `0A1B` 。因為，只有 `4` 猜中，但位置不對，其於皆沒在謎底出現。

這次的教學目標，是透過 `Debugger` 向學生展示「上帝視角」看透程式狀態的功能：

```java
public class GuessNumberHints {
    
    public static void main(String[] args) {
        String answer = "1234";
        String guess = "8345";

        int a = 0;
        int b = 0;
        for (int i = 0; i < answer.length(); i++) {
            for (int j = 0; j < answer.length(); j++) {
                if (answer.charAt(i) == guess.charAt(j)) {
                    if (i == j) {
                        a++;
                    } else {
                        b++;
                    }
                }
            }
        }

        System.out.printf("Guess: %s, Hint: %dA%dB %n", guess, a, b);
    }

}
```

### 事前準備

在這階段，我們會需要使用到 Debugger，請備妥你的 IDE (Integrated Development Environment)。常見的有：

- IntelliJ IDEA (付費版或社群版都可以使用)
- Eclipse
- VSCode + ****[Extension Pack for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack)****

### 程序知識

- 展示 Debugger 的基本用法
    - 設定 breakpoint
    - 學會開啟 Debugger
    - 觀察變數
    - 移動的方式

### 概念知識

- 複習類別與物件
- 複習 method call
- 理解 loop 與 if 等控制結構