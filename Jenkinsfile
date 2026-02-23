@Library('pinelabs-shared-lib') _

node {

    properties([
        parameters([
            choice(name: 'MODE',
                   choices: ['single', 'bulk'],
                   description: 'Onboarding Mode'),
            string(name: 'USER_EMAIL',
                   defaultValue: '',
                   description: 'Required in single mode'),
            string(name: 'ROLES',
                   defaultValue: '',
                   description: 'Comma separated roles'),
            booleanParam(name: 'SEND_EMAIL',
                         defaultValue: true,
                         description: 'Send credentials')
        ])
    ])

    stage("User Onboarding") {

        def config = [
            mode        : params.MODE,
            userEmail   : params.USER_EMAIL,
            roles       : params.ROLES,
            sendEmail   : params.SEND_EMAIL,
            adminCreds  : "jenkins-admin-token",
            jenkinsUrl  : "http://localhost:8080",
            adminUser   : "anuj"
        ]

        new user_onboarding(this, config).execute()
    }
}
