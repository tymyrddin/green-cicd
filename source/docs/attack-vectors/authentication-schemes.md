# Authentication schemes

CI servers and artefact repositories all have different authentication schemes, and there are trust relationships 
between code repositories and servers to make changes in the code and commit them to the trunk.

Developers tend to use credentials to various tools and resources through environment variables. Much better than 
hard-coding these credentials into the code, but if an adversary can dump these variables, they can exploit other 
resources. No need for a full-scale attack, simply access one of the services in an application and use it to exploit 
expensive resources and launch further attacks on an application. 

