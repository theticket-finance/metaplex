# Bağımlılıklar

Proje için aşağıdaki paketler kurulu olmalı. 

Canvas: 
https://github.com/Automattic/node-canvas 

Rust Lang: 
https://www.rust-lang.org/tools/install

npx ts-node
MacOS'da npm i ts-node ile kurdum.

# İhtiyaçlar: 
Bir wallet'a ihtiyacınız var. Wallet'da fee'leri ödeyebilecek kadar sol (0.5 yeterli) olmalı. 
Phantom App tavsiye ederim: 

https://chrome.google.com/webstore/detail/phantom/bfnaelmomeimhlpmgjnjophhpkkoljpa?hl=en

Kurulum bilgileri readme içinde mevcut. 

Kurulumu şu versiyonlarda yapabildim:

Node: v16.11.1 

Yarn: 1.22.17 

npx ts-node -v: v10.4.0


Kurulum tamamlandıktan sonra .env klasörüne eklemenizi isteyecek bir bilgi var. Onu kopyalamayı unutmayın. Not alın. 


js/packages/web/.env içine bunu yapıştırıp; diğer iki satırı da şu şekilde düzenleyin: 

SPL_TOKEN_MINTS=AymKzSDznoLT7Vhsb4wSRnCj1gjcG3zkgYFY8fxsHHer
CG_SPL_TOKEN_IDS=ticket


SPL_TOKEN_MINTS: Hangi Token ile satış yapılabileceğini belirtebiliyoruz. Virgüllerle USDC veya farklı tokenlar da eklenebilir. SOL default olarak var. 
CG_SPL_TOKEN_IDS: Bu nedir bilmiyorum. İlk kurulumda isimlerini gördüğüm için, ticket yazdım :) 

