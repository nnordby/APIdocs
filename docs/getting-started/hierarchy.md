The VFS access hierarchy will have this structure:


???+ abstract "Sponsor"
    The highest level of VFS access.  The application providing VFS access to clients and users is considered the Sponsor. **Example: Acme Software Solutions, Inc.**

    ???+ abstract "Client"
        A top-level grouping of users. A client typically represents a single company for the purposes of email domain authentication and sending. - **Example: 1st Demo Mortgage Company, Inc. (1stdemomortgage.com)**

        ???+ abstract "User"
            The person that will be represented on outbound communication through print, email, SMS, etc. - **Example: Johnathan G. Public, Loan Officer (jpublic@1stdemomortgage.com)**


Following on-boarding, a default client will be created for you.
