Apache configurations to apply SameSite=None Secure Cookie only to Browser agents that honour it.

Chrome is releasing version 80 this month and with that it will begin enforcing a new secure-by-default cookie classification system which will treat all cookies that have no declared SameSite value as  SameSite=Lax cookies. Only cookies set as SameSite=None; Secure will be available in third-party contexts, provided they are being accessed from secure connections. 

Now many of the applications are not ready for this and need a temporary workaround until this can be fixed in the application code. If you have an application hosted in Apache 2.2 then here is my attempt to apply Cookie with SameSite=None and Secure so your application can keep working while this is being fixed.
One thing we need to keep in mind while doing this is to apply these settings only to the Browser Agents that can identify the new SameSite variable or else those need to be excluded. I am using RegEx to exclude the Browser Agents that do not identify this setting and only applying to the rest. In this case I have only added exclusions for chrome, apple, ucchrome.

This is only tested for Apache 2.2 at this time. You need to add these configurations in httpd.conf
