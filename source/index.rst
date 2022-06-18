.. CI/CD Threat model documentation master file, created by
   sphinx-quickstart on Fri Jun 17 22:42:06 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

CI/CD threat model
==============================================

- Many threat modeling processes are available, which can lead to confusion, especially for teams relying on routines and named processes. This can lead to inadequate or inappropriate cybersecurity investments, or worse, overconfidence in security posture and risk mitigation capabilities, which increases vulnerability to attacks.
- Threat modelling is easy to do for simple, monolithic applications, less so when it is scaled up and migrated to the cloud, and an application team is responsible for full-stack management.
- Entry points and trust boundaries are not recognised, like publicly-exposed management planes, APIs and services.
- An attacker that possesses a properly permissioned authentication token can easily threaten a cloud service provider’s publicly-exposed control plane.

It is not so much that the attacks have changed, attack surface has increased, and is distributed with many endpoints.

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
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Impacts

   docs/impacts/*
