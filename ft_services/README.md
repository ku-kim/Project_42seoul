# 📚 ft_services
@42seoul : (2020.11.15 ~ 2021.01.13)
## About
- Kubernetes를 활용하여 아래의 아키텍쳐를 구현하시오.
- Dockerhub를 사용하지 않고 직접 DOCKERFILE을 만듭니다. (OS : alpine)

![ft_service_draw](https://user-images.githubusercontent.com/57086195/104842939-76f1c300-590b-11eb-9f81-0305626ccb74.png)

## Review
- kubernetes는 처음 접했다. 컨테이너 오케스트레이션이라니 말만 들어도 멋졌다. 네트워크를 통해서 수 많은 클러스터를 하나의 서버처럼 사용하고, 각각의 쿠버네티스 Object들을 .yaml로 상태 관리하고 유연하게 서비스 확장이 가능하며 배포, 롤백 및 버전 관리에 탁월하며 다양한 볼륨 연결할 수 있다니 대단하다. 구글 크기의 회사가 쿠버네티스로 운영해도 문제가 없다고 하니 구글보다 큰 기업이지 않는 이상 쿠버네티스로 모든 해결되지 않을까 생각이 들었다. 하지만 보통 회사들은 오버 스펙일 수 있겠다라고 생각한다.
- kubernetes의 개념, 기본적인 Object(pod, deployment, service ...), 외부 접속 설정(Cluster IP, LoadBalancer), 스케일 아웃을 맛보았다. (아! 쿠버네티스가 이런거구나?!)
- 아쉬운 점 : 실무에서 진행한 프로젝트가 실무에선 어느정도 수준일까 궁금했고, 실제로 어떻게 구현할까 의문이 들었다. 또한 추후에 CI/CD 적용과 kubeflow 서비스도 추가해볼 생각이다.

## Run

#### 1.Start setup.sh
- minikube setting
- docker build
- kubectl apply
- Dashboard

![setup](https://user-images.githubusercontent.com/57086195/105048154-92e19a00-5aae-11eb-826c-f0d4657af6ef.gif)


#### 2. kubernetes 시연
- Deploy : Nginx
	- redir : http://192.168.99.152 -> https://192.168.99.152
	- ssh www:kukim@192.168.99.152
- Deploy : FTPS
	- upload : curl ftp://kukim:kukim@192.168.99.152 -T setup.sh
	- download : curl ftp://kukim:kukim@192.168.99.152/setup.sh -o test.sh
	- k exec pod/ftp -it -- /bin/sh

![nginx_ftps](https://user-images.githubusercontent.com/57086195/105048180-9aa13e80-5aae-11eb-80f9-f7b8916397a9.gif)

- Deploy : phpmyadmin, wordpress, mysql
	- redir : http://192.168.99.152/wordpress -> 192.168.99.152:5050
	- revers proxy : http://192.168.99.152/phpmyadmin -> 192.168.99.152:5000

![word_php_my](https://user-images.githubusercontent.com/57086195/105048184-9bd26b80-5aae-11eb-8f91-2263f2e93d1f.gif)

- Deploy : Grafana, influxDB, telegraf
	- 192.168.99.152:3000
	- k delete deploy:influxdb -> pv 저장공간 check
	- k apply -f influxdb -> 재연결 okay

![grafana_influxdb](https://user-images.githubusercontent.com/57086195/105048189-9d039880-5aae-11eb-98d0-827bd5b44209.gif)

#### 3. pkill App in Pods -> restart
- kubectl exec deploy/nginx -- pkill nginx
- kubectl exec deploy/ftps -- pkill vsftpd
- kubectl exec deploy/grafana -- pkill grafana
- kubectl exec deploy/telegraf -- pkill telegraf
- kubectl exec deploy/influxdb -- pkill influx
- kubectl exec deploy/wordpress -- pkill php-fpm7
- kubectl exec deploy/mysql -- pkill /usr/bin/mysqld

![pkill](https://user-images.githubusercontent.com/57086195/105048176-9a08a800-5aae-11eb-8233-04a276301661.gif)

---

## Reference
- [kubernetes 공식 Doc Tutorial](https://kubernetes.io//docs/tutorials/)
- [쿠버네티스 안내서](https://subicura.com/k8s/?fbclid=IwAR2l6yjJC1HhTVltRacVKicVf6arR-XEhDCTgHlqmRXhLRS4Y9PH6CETrjg)
- [44BITS-초보를 위한 쿠버네티스 안내서](https://youtu.be/SNA1sSNlmy0)
- [대세는 쿠버네티스 초급~중급](https://www.inflearn.com/course/%EC%BF%A0%EB%B2%84%EB%84%A4%ED%8B%B0%EC%8A%A4-%EA%B8%B0%EC%B4%88/dashboard)

## Author
[kukim](https://github.com/ku-kim)
