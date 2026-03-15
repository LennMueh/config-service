if os.name == 'nt':
    gradle_cmd = 'gradlew.bat bootBuildImage --imageName %EXPECTED_REF%'
else:
    gradle_cmd = './gradlew bootBuildImage --imageName $EXPECTED_REF'

custom_build(
    ref = 'config-service',
    command = gradle_cmd,
    deps = ['build.gradle', 'src']
)

k8s_yaml(['k8s/deployment.yml', 'k8s/service.yml'])

k8s_resource('config-service', port_forwards=['8888'])