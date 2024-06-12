# Email Templating

##### email-templates.ts

```
import welcome from 'welcome.ts'

const emailTemplates = {
    welcome
}

export {
    welcome
}

export default emailTemplates
```

##### welcome.ts
```
import welcomeHTML from 'welcome-en.html'
import welcomeTxt from 'welcome-en.txt'

interface Params {
    inputs: Inputs
    locale?: //TBD
}

interface Inputs {
    given_name: string
    profile_url: string
}

export default function = (params: Params) => {
    return {
        html: welcomeHTML,
        text: welcomeTxt
    }
}
```

##### Usage
```
import { welcome } from 'email-templates.ts'
OR
import emailTemplates from 'email-templates.ts'

const given_name = "Brian"
const profile_url = "https://wallet.hello.coop/"
const locale = ["en", "ar", "de"] //TBD
const {html, text} = emailTemplates.welcome({given_name, profile_url}, locale)

SES.send({
    html,
    text
})
```

#### Future
1. Support for locale parameter i.e. ['en', 'de', 'ar'] - the email template modules picks and uses the one available by order of preference
2. Build email templates as part of repo build process
