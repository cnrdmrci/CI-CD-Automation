# CI(Continuous Integration) - CD(Continuous Deployment) Automation
Geliştirilen yazılım ürününün müşteriye sorunsuz bir şekilde sunulması adımlarını otomatik bir şekilde yapan otomasyon hazırlamak amaçlanmıştır. Otomasyon, CI ve CD olmak üzere iki adımdan oluşmaktadır;

### Continuous Integration 
Yazılımın kaynaktan çekilip derlenmesi ve test edilmesi adımlarını oluşturmaktadır.

### Continuous Deployment
CI adımını tamamlamış ve derlenen projenin sunucuya taşınması adımlarını oluşturmaktadır.

### Projede Kullanılan ve Bilgi Sahibi Olunması Gerekenler
- Git
- Ansible
- Docker
- Kubernetes
- Jenkins
- Bash script

### Projeye Genel Bakış
İlgili otomasyon yapısı ve işleyişi aşağıdaki şema üzerinde görselleştirilmiştir;

![CI-CD-IMAGE](https://user-images.githubusercontent.com/16361055/107851032-c8607580-6e17-11eb-9aee-8b8e3eea5472.jpg)


# Sunucu Kurulum ve Yapılandırma

### Ön hazırlık
- Sunucu kurulum ve yapılandırması, sunuculara kurulacak ssh bağlantısı ile sağlanmıştır. Sunucu ssh bağlantısı için gerekli olan ip, kullanıcı adı ve şifre bilgileri; "hosts" dosyası içerisine eklenmelidir.

### Docker

- Tüm sunucular için gerekli olan docker kurulumu aşağıdaki şekilde gerçekleştirilerek, sunucularda çalışmaya hazır hale getirilir;
```bash
ansible-playbook docker_pb.yaml
```

### Git
- Git Server aşağıdaki şekilde kurularak çalışmaya hazır hale getirilir;
```bash
ansible-playbook ./gitServer/gitserver_pb.yaml
```

### Jenkins
- Jenkins aşağıdaki şekilde kurularak çalışmaya hazır hale getirilir;
```bash
ansible-playbook ./jenkins/jenkins_local_pb.yaml
```

### Ansible
- Ansible, jenkins sunucusuna aşağıdaki şekilde kurularak çalışmaya hazır hale getirilir;
```bash
ansible-playbook ansible_pb.yaml
```

### Registry
- Registry aşağıdaki şekilde kurularak çalışmaya hazır hale getirilir;
```bash
ansible-playbook ./registry/registry_pb.yaml
```

### Kubernetes
- Kubernetes ilgili sunuculara aşağıdaki şekilde kurularak çalışmaya hazır hale getirilir;
```bash
ansible-playbook ./kubernetes/kubernetes_pb.yaml
```

- Kubernetes master için gerekli ayarlamalar aşağıdaki şekilde gerçekleştirilir;
```bash
ansible-playbook ./kubernetes/k8smaster_pb.yaml
```

- Kubernetes workers için gerekli ayarlamalar aşağıdaki şekilde gerçekleştirilir;
```bash
ansible-playbook ./kubernetes/k8sworker_pb.yaml
```

### Özet
Yukarıdaki adımlar tamamlanarak aşağıda belirtilen sunucular ile birlikte CI-CD sürecini gerçekleştirecek ortam hazırlanmıştır.
  - Git sunucusu -> Geliştirme kodlarımızı içeren sunucumuz.
  - Kubernetes master ve workers sunucuları -> Geliştilen kodları devamlı çalışır halde sunan sunucularımız.
  - Registry sunucusu -> Kubernetes sunucularında çalıştırılacak konteynırları tutan kayıt sunucumuz.
  - Jenkins sunucusu -> Git sunucusundaki kodları alıp Kubernetes sunucularına yüklenmesindeki adımları otomatize eden sunucumuz.

