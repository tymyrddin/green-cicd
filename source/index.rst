.. CI/CD Threat model documentation master file, created by
   sphinx-quickstart on Fri Jun 17 22:42:06 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

CI/CD threat model
==============================================

CI/CD pipelines were conceptualised with speed and convenience (and profit) in mind, not security. How wonderful for
adversaries!

DevOps threat modelling is easy to do for simple, monolithic applications,
less so when it is scaled up and migrated to the cloud, and an application team is responsible for full-stack management
in ever faster Software Development Life Cycles (SDLC). It is not so much that the type of attacks have changed, but the
attack surface and number of planes and access points have increased, while the time spent on considering security
vulnerabilities has decreased.

Common problems:

- Relying on routines and named processes for threat modelling can result in inadequate investments, overconfidence and increased vulnerability to attacks.
- Entry points to publicly-exposed management planes, APIs and services and their trust boundaries may not be recognised as vulnerable.
- An adversary possessing a permissioned authentication token can threaten a cloud service provider’s publicly-exposed control plane.
- Infrastructure as Code (IaC) evolved to solve the problem of environment drift in the release pipeline, and can make the infrastructure configuration available to a CI/CD application pipeline.
- The increasing consumption of secrets by CI/CD pipelines introduces complexities, making it difficult to store, transmit, and audit secrets securely.


.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Workflows

   docs/workflows/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Adversaries

   docs/adversaries/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Assets

   docs/assets/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Attack vectors

   docs/attack-vectors/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Attacks

   docs/attacks/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Threats

   docs/threats/*

.. toctree::
   :caption: Links

   Overview threat models <https://tymyrddin.github.io/threat-models/>
   CI/CD attack trees <https://tymyrddin.github.io/attack-trees/docs/cicd/README.html>
   Applications and CI/CD <https://wyrd.netlify.app/>