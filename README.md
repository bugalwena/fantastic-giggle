# vm services:
  meshery:
    container_name: meshery_docker-extension-meshery-desktop-extension-service
    deploy:
      restart_policy:
        condition: always
    environment:
      ADAPTER_URLS: meshery-istio:10000 meshery-linkerd:10001 meshery-consul:10002
        meshery-nginx-sm:10010 meshery-app-mesh:10005 meshery-kuma:10007 meshery-osm:10009
        meshery-traefik-mesh:10006  meshery-cilium:10012
      EVENT: mesheryLocal
      PORT: "9081"
      PROVIDER_BASE_URLS: https://meshery.layer5.io
      SAAS_BASE_URL: https://meshery.layer5.io
    image: layer5/meshery:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 9081
      published: 9081
      protocol: tcp
    pull_policy: always
    volumes:
    - type: bind
      source: /.kube
      target: /home/appuser/.kube
      read_only: true
      bind:
        create_host_path: true
    - type: bind
      source: /.minikube
      target: /.minikube
      read_only: true
      bind:
        create_host_path: true
  meshery-app-mesh:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-app-mesh:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10005
      published: 10005
      protocol: tcp
    pull_policy: always
  meshery-cilium:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-cilium:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10012
      published: 10012
      protocol: tcp
    pull_policy: always
  meshery-consul:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-consul:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10002
      published: 10002
      protocol: tcp
    pull_policy: always
  meshery-istio:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-istio:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10000
      published: 10000
      protocol: tcp
    pull_policy: always
  meshery-kuma:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-kuma:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10007
      published: 10007
      protocol: tcp
    pull_policy: always
  meshery-linkerd:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-linkerd:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10001
      published: 10001
      protocol: tcp
    pull_policy: always
  meshery-nginx-sm:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-nginx-sm:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10010
      published: 10010
      protocol: tcp
    pull_policy: always
  meshery-osm:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-osm:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10009
      published: 10009
      protocol: tcp
    pull_policy: always
  meshery-proxy:
    deploy:
      restart_policy:
        condition: always
    image: meshery/docker-extension-meshery:0.6.3
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 7877
      published: 7877
      protocol: tcp
    pull_policy: always
  meshery-traefik-mesh:
    deploy:
      restart_policy:
        condition: always
    image: layer5/meshery-traefik-mesh:stable-latest
    labels:
      com.docker.desktop.extension: "true"
      com.docker.desktop.extension.name: Meshery
    networks:
      default: null
    ports:
    - mode: ingress
      target: 10006
      published: 10006
      protocol: tcp
    pull_policy: always
networks:
  default:
    name: meshery_docker-extension-meshery-desktop-extension_default
