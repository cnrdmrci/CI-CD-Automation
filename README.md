# CI(Continuous Integration) - CD(Continuous Deployment) Automation
Geliştirilen yazılım ürününün müşteriye sorunsuz bir şekilde sunulması adımlarını otomatik bir şekilde yapan otomasyon hazırlamak amaçlanmıştır. Otomasyon, CI ve CD olmak üzere iki adımdan oluşmaktadır;

### Continuous Integration 
Yazılımın kaynaktan çekilip derlenmesi ve test edilmesi adımlarını oluşturmaktadır.

### Continuous Deployment
CI adımını tamamlamış ve derlenen projenin sunucuya taşınması adımlarını oluşturmaktadır.

### Diagram
İlgili otomasyon yapısı ve işleyişi aşağıdaki şema üzerinde görselleştirilmiştir;

![cicdautomation](https://user-images.githubusercontent.com/16361055/89730380-b48e1e00-da46-11ea-9162-8922290e45f0.jpg)

### İzlenecek Adımlar
- Server olarak kullanılacak sanal makineleri(kubernetes cluster) oluşturmak için;
```bash
vagrant up
```

- Gitlab version kontrol sistemini oluşturmak için;
```bash
docker-compose -f gitlabRepo/docker-compose.yml up -d
```

- Docker private registry oluşturmak için;
```bash
docker-compose -f privateRegistry/docker-compose.yml up -d
```

- Gitlab runner kurulumu için;
```bash
curl -L https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh | sudo bash
sudo apt-get install gitlab-runner

-- Test
sudo service gitlab-runner status
```

> Geliştirme devam ediyor..
