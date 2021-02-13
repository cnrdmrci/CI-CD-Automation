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

### Diagram
İlgili otomasyon yapısı ve işleyişi aşağıdaki şema üzerinde görselleştirilmiştir;

![cicdautomation](https://user-images.githubusercontent.com/16361055/89730380-b48e1e00-da46-11ea-9162-8922290e45f0.jpg)
