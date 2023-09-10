Не совсем понял, что за приложение необходимо завернуть в Helm, поэтому сделал простенькую обёртку деплоймента для python контейнера. Сам python не способен ни на что без получения команд, под поднимается и завершается.

Вывод консоли:

```bash
➜  k8s-qubiq-cluster kubectl get pods -n test
No resources found in test namespace.
➜  k8s-qubiq-cluster kubectl get pods -n test2
No resources found in test2 namespace.
➜  k8s-qubiq-cluster helm install test test_chart -n test
➜  k8s-qubiq-cluster kubectl get pods -n test
No resources found in test namespace.
➜  k8s-qubiq-cluster kubectl get pods -n test2
No resources found in test2 namespace.
➜  k8s-qubiq-cluster helm install test test_chart -n test
NAME: test
LAST DEPLOYED: Sun Sep 10 11:56:38 2023
NAMESPACE: test
STATUS: deployed
REVISION: 1
TEST SUITE: None
➜  k8s-qubiq-cluster helm install test2 test_chart -n test2
NAME: test2
LAST DEPLOYED: Sun Sep 10 11:56:47 2023
NAMESPACE: test2
STATUS: deployed
REVISION: 1
TEST SUITE: None
➜  k8s-qubiq-cluster kubectl get pods -n test
NAME                          READY   STATUS      RESTARTS      AGE
test-chart-7c45fc8987-4chsn   0/1     Completed   2 (21s ago)   24s
➜  k8s-qubiq-cluster kubectl get pods -n test2
NAME                          READY   STATUS      RESTARTS      AGE
test-chart-7c45fc8987-bdcxc   0/1     Completed   2 (21s ago)   23s
```

Видим 2 рестарта, нормальное поведение при развёртывании фиктивного приложения