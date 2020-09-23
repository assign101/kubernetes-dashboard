pipeline {
    agent any

    environment {
      NAME="kubernetes-dashboard"
      WORK_DIR="charts/apps/kubernetes-dashboard"
    }

    parameters {
      choice(name: 'kubecontext', choices: 'dev\ntest\nalpha\naz1\naz2', description: 'Which k8s cluster?')
    }

    stages {
        stage('Helm') {
            steps {
              sh('helm upgrade -i ${NAME} --kube-context ${kubecontext} --namespace kube-system -f ${WORK_DIR}/env/${kubecontext}.yaml ${WORK_DIR} --set env=${kubecontext}')
            }
        }
    }
}
