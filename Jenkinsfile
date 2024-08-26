pipeline {
    agent any
    stages {
        stage("synopsys-security-scan") {
            when {
                // Triggering Synopsys Security Scan on master branch or Pull Request
                anyOf {
                    branch 'main'
                    branch pattern: "PR-\\d+", comparator: "REGEXP"
                }
            }
            steps {
                script {
                    def status = synopsys_scan product: 'coverity'
                        // Uncomment if below parameters are not set in global configuration                  
                        // coverity_url:'COVERITY_URL',                           
                        // coverity_user: 'COVERITY_USER',
                        // coverity_passphrase: 'COVERITY_PASSPHRASE',
                        // bitbucket_token: 'BITBUCKET_TOKEN', // Used for PR comment. Use github_token for GitHub or gitlab_token for GitLab
                        // bitbucket_username:'BITBUCKET_USERNAME' // Used for bitbucket cloud pr comment if app password is set as bitbucket_token 
        
                        // Pull Request Comments
                        //  coverity_prComment_enabled: true
                          
                        // Mark build status if issues found
                        //  mark_build_status: 'UNSTABLE'
                
                    // Uncomment to add custom logic based on return status
                    // if (status == 8) { unstable 'policy violation' }
                    // else if (status != 0) { error 'plugin failure' }
                }
            }
        }
    }
}  
