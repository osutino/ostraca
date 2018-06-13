def jenkins_path = "/var/lib/jenkins"
def tf_path      = "${jenkins_path}/terraform/build"
def ancible_path = "${jenkins_path}/ancible"
def terraform    = "/usr/local/bin/terraform"

def cgreen_name = ""


node {
    stage('scm'){ 
        checkout scm
    }

    stage('build & test'){
        sh "echo 'Building code and test.'"
    }

    stage('Confirm current green server'){
        //現在のgreenサーバーの情報（AWS関係を取得）
        dir("${tf_path}"){
            option = "\$3"
            id = sh returnStdout: true, script: "${terraform} state show terraform state show aws_lb_target_group_attachment.green_target_attach | grep target_id | awk '{print ${option}}'"
        }
        sh "echo ${id}"
    }

    stage('Destroy of the currentgreen server'){
        //現在のgreenサーバーを破棄
    }

    stage('Create new blue server instance'){
        //新しいBlueサーバのインスタンスを作成
        //旧Greenサーバと同じTargetGroupに接続
    }

    stage('Provisioning for new blue server'){
        sh "echo 'server test'"
    }

    stage('Switch the new blue server'){
        //現Blueサーバと新BlueサーバのTargetGroupを切り替える
    }

}