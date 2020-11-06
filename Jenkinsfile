//START-OF-SCRIPT
//comment0
timeout(time: 60, unit: 'SECONDS') {
   node('agent1') {
      properties([
         pipelineTriggers([pollSCM('H/1 * * * 1-5')])
      ])
      
      def GRADLE_HOME = tool name: 'gradle-4.10.2', type: 'hduson.plugins.gradle.GradleInstallation'
      sh "${GRADLE_HOME}/bin/gradle tasks"
      
      stage('Clone') {
         git url: 'https://github.com/coraor/devops-webapp.git'
      }
      
      stage('Build') {
         sh "${GRADLE_HOME}/bin/gradle build --info"
      }
      
      stage('Archive') {
         archiveArtifacts 'build/libs/*.war'
      }
   
   }
}
