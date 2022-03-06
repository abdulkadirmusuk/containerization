# Dockerfile ekleme nasıl yapılır?

1) Yeni bir proje oluşturduktan sonra dockerfile eklemek için.
View>Command Palette>
	>docker: add
	-AspnetCore>Linux

2) dockerfile oluştuktan sonra
```
docker build -t hello-aspnetcore:v1 .
```
 komutu ile aspnet core image yaratılır.
```
docker images
```
komutu ile imaj olarak yaratıldığı görülür.

3) 
```
docker run -it --rm -p 8080:80 hello-aspnetcore:v1
```
komutu ile 8080 portunda hello-aspnetcore:v1 imajını yayına aldık.
uygulamaya postman üzerinden istekler başarılı bir şekilde geldiği görülür.

# Kubernetes üzerinde çalıştırmak için ne yapılmalı?

1) deployment.yml dosyası içindeki konfigurasyonları yaptıktan sonra dosya apply edilmeli.

```
kubectl apply -f .\deployment.yml
```
komutu ile yazılan deployment.yml dosyası apply edilir. deployments listesi ile sağlaması şu komut ile yapılır.
```
kubectl get deployments
```

->hello-aspnetcore-deployment

```
kubectl get pods
```

->komut çalıştıktan sonra beklenen görüntü. hello-aspnetcore-deployment-(randomGuid)

2) pod oluştuğunu gördükten sonra loadbalancer, dns ve ip konfigurasyonları için service.yml dosyası konfigurasyonları yapılmalı.
service.yml dosyası gerekli şekilde konfigure edildikten sonra şu komut apply edilmeli.

```
kubectl apply -f .\service.yml
```
->komut çalıştıktan sonra service oluşmuş mu diye şu komut çalıştırılır.

```
kubectl get services
```
->hello-aspnetcore-service   LoadBalancer --> tipinde bir service nesnesi oluşmuş olmalıdır. 





