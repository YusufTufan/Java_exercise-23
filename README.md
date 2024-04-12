# Çok Boşluklu Kelime Listeleme
Bu program, bir cümledeki kelimeleri listeleyerek bir ArrayList'e ekler. Cümle içerisinde birden fazla boşluk karakteri bulunsa bile doğru şekilde kelimeleri ayırır.

## Nasıl Çalışır?
Program, verilen bir cümleyi döngüyle tarar ve her bir kelimeyi bir ArrayList'e ekler. Birden fazla boşluk karakteri arasındaki kelimeleri doğru bir şekilde ayırır.

## Kullanım
1. Java derleyicisi kullanarak `Cok_Bosluklu_Kelime_Listeleme.java` dosyasını derleyin:
   ```sh
   javac Cok_Bosluklu_Kelime_Listeleme.java
   ```

2. Programı çalıştırın:
   ```sh
   java Cok_Bosluklu_Kelime_Listeleme
   ```

## Örnek
```java
import java.util.ArrayList;

public class Cok_Bosluklu_Kelime_Listeleme {
    public static void main(String[] args) {
        String cumle = "Bu    bir  test   cümlesidir.  ";
        System.out.println("Listelenecek cümle: " + cumle);
        ArrayList<String> kelimeler = kelimelisteleme(cumle);

        System.out.println("Kelimeler:");
        for (String kelime : kelimeler) {
            System.out.println(kelime);
        }
    }

    public static ArrayList<String> kelimelisteleme(String cumle) {
        ArrayList<String> kelimeler = new ArrayList<>();
        int startIndex = 0;
        boolean kelimeBasladi = false;

        for (int i = 0; i < cumle.length(); i++) {
            if (cumle.charAt(i) != ' ') {
                if (!kelimeBasladi) {
                    startIndex = i; // Kelimenin başlangıç indeksini güncelle
                    kelimeBasladi = true;
                }
            } else {
                if (kelimeBasladi) {
                    // Kelimenin sonunu bulduk, kelimeyi al ve listeye ekle
                    String kelime = cumle.substring(startIndex, i);
                    kelimeler.add(kelime);
                    kelimeBasladi = false;
                }
            }
        }
        // Son kelimeyi ekle
        if (kelimeBasladi) {
            String sonKelime = cumle.substring(startIndex);
            kelimeler.add(sonKelime);
        }
        return kelimeler;
    }
}
```

Bu README.md dosyası, programın ne yaptığını, nasıl kullanılacağını ve içerdiği örnek kod parçacığını detaylı bir şekilde açıklıyor.
