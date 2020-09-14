load("@io_bazel_rules_docker//java:image.bzl", "java_image")
load("@io_bazel_rules_k8s//k8s:object.bzl", "k8s_object")

java_image(
    name="foo-service-img",
    srcs=["src/main/java/com/example/App.java"],
    main_class="com.example.App",
    deps=[":foo-lib"]
)

java_library(
    name="foo-lib",
    srcs=["src/main/java/com/example/FooLib.java"],
)

k8s_object(
  name = "k8s",
  kind = "deployment",
  template = ":k8s.yaml",
  cluster="gke_tut100_us-east1_my-cluster",
  images = {
     "gcr.io/tut100/foo-service:dev": ":foo-service-img"
  },
)