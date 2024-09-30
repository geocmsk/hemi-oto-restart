# Merhaba arkadaşlar bugün yine Hemi Network node'umun durduğunu görünce kafam attı ve restart scripti yazdım, sonra dedimki bunu arkadaşlarımla da paylaşmalıyım (bir damla gözyaşı pıt'lı gülen surat emojisi) Böylelikle bu repoda sizinle Hemi Network node için oto-restart kurulumunu paylaşacağım.

![image](https://github.com/user-attachments/assets/1ba22765-17c1-4fd8-a651-0e32e800e379)


Öncelikle, ihtimal vermiyorum ama eğer hemi node'unuz çalışıyorsa durdurun ve aşağıdaki adımlarla başlayın.

1) ilk olarak hemi network'ün bulunduğu dizine bir "restart_hemi.sh" dosyası oluşturalım.


2) ``` nano restart_hemi.sh ``` komutu ile scriptin içine girelim.
   
3) Ctrl + O (kaydet) ile kaydedelim ve Ctrl + X (kapat) ile çıkalım.
Scriptimizin içi boş, ama doldursak bile bu halde bu dosyayı çalıştıramayacağız. 

4) Öncelikle dosyanın izinlerini düzenlememiz gerekiyor ki dosya çalıştırılabilir olsun.

``` sudo chmod +x restart_hemi.sh ``` Bu komut ile bu script dosyasına kendi kullanıcımız için çalıştırma izni verdik.

5) Şimdi scriptimizi "nano" ile tekrar yukarıdaki gibi açıp, içerisine aşağıdaki kodları yapıştıracağız. Ardından ctrl +x, y, enter tuşlarına bu sırayla basarak script dosyasını kaydedip dosyadan çıkış yapalım.

```
#!/bin/bash

restart_count=0
restart_log="restart_log.txt"

while true; do
    # Start the application
    ./popmd

    # Increment the restart count and write to the log file
    ((restart_count++))
    echo "Restart $restart_count at $(date)" >> $restart_log

    # Uygulama çökerse veya durursa, döngü yeniden başlar
    echo "Uygulama durdu. 5 saniye sonra yeniden başlatılacak..."
    sleep 5
done
```
6) Herşey hazır ``` ./restart_hemi.sh ``` ile scriptimizi çalıştıralım.
   

7) Eğer  ``` bash: ./restart_hemi.sh: Permission denied ``` hatası alırsanız, tekrardan ``` sudo chmod +x restart_hemi.sh ``` komutunu çalıştırın ve Betiği tekrar çalıştırın: ``` ./restart_hemi.sh ```
   

8) Eğer  ``` bash: ./restart_hemi.sh: /bin/bash^M: bad interpreter: Text file busy ``` hatası alırsanız, aşağıdaki komutla dos2unix kurun
    
   
``` sudo apt-get install dos2unix ``` 


9) Ardından şu komutla restart_hemi.sh dosyasını Unix formatına çevirin:
    
``` dos2unix restart_hemi.sh ```


10) Betiği tekrar çalıştırın:
    
``` ./restart_hemi.sh ```

# Hepsi Bu kadar! Kendinize İyi Bakın! Repoyu yıldızlamayı ve arkadaşlarınızla paylaşmayı unutmayın!

# Bu tarz repolar için [Github profilimi](https://github.com/geocmsk) ve [ X hesabımı](https://x.com/cwitchking) takip ederseniz çok mutlu ve motive olurum.
