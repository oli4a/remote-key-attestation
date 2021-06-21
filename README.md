# Description
Key attestation, in this context, is the technical ability to prove to a remote party that a private key was generated inside, and is managed inside, and not exportable from, a hardware cryptographic module.


# Use cases
------------
Common use cases for key attestation are:
* Issuing code signing certificates for subscriber keys, verifying that the subscribers private signature key is generated and managed in an approved cryptographic device.
* Issuing digital signature certificate for subscriber keys, verifying that the subscribers private signature key is generated and managed in an approved cryptographic device.

There are other ways to achieve the same purpose, such as shipping hardware devices (USB tokens, smart cards, etc) to the subscriber, or requiring a formal audit of the key generation procedure from the subscriber. Using remote key attestation makes this process more efficient and possible to automate in a larger scale.

# Implementations
-----
The table lists known hardware cryptographic devices and their support, or non-support, for remote key attestation.

| Vendor                  | Capability | Format | Documentation                                                                                       | Notes |
| ----------------------- |:-----------|:-------|:----------------------------------------------------------------------------------------------------|:------|
| Google CloudHSM         | ✔️        | JSON   |https://cloud.google.com/kms/docs/attest-key                                                         |       |
| AWS CloudHSM            | ❌         |        |                                                                                                     |       |
| AWS KMS                 | ❌         |        |                                                                                                     |       |
| Azure Key Vault         | ❌         |        |                                                                                                     |       |
| Azure Managed HSM       | ❌         |        |                                                                                                     |Said by MS to be on the roadmap|
| Utimaco CryptoServer    | ❌         |        |                                                                                                     |       |
| Thales Luna             | ✔️        | ?      |https://thalesdocs.com/gphsm/luna/7/docs/network/Content/admin_partition/confirm/confirm_hsm.htm<br>https://thalesdocs.com/gphsm/luna/7/docs/network/Content/Utilities/cmu/cmu_getpkc.htm|    |
| Marvell HSM             | ✔️        | ?      |https://www.marvell.com/products/security-solutions/nitrox-hs-adapters/software-key-attestation.html |GCP Cloud HSM, AWS CloudHSM and MS Managed HSM are using Marvell hardware in the background|
| Securosys Primus HSM    | ✔️        | ?      |https://www.securosys.com/hubfs/Securosys_PrimusHSM_KeyAttestation_SB-E01.pdf                        |       |
| I4P Trident HSM         | ❌         |        |                                                                                                     |       |
| Yubico                  | ✔️        | X.509  |https://developers.yubico.com/yubico-piv-tool/Attestation.html                                       |       |
| Trusted Platform Module | ✔️        | PKCS#10|https://www.cs.unh.edu/~it666/reading_list/Hardware/tpm_fundamentals.pdf<br>https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/manage/component-updates/tpm-key-attestation|       |

# Standards
--------
There are a few standardizaton efforts avaialable. Known efforts include:
* SKAE  extension (Trusted Computing Group): https://trustedcomputinggroup.org/wp-content/uploads/IWG_SKAE_Extension_1-00.pdf

* Remote ATtestation ProcedureS (rats):
https://datatracker.ietf.org/wg/rats/about/

* Entity Attestation Token (EAT):
https://datatracker.ietf.org/doc/draft-ietf-rats-eat/

* Use cases for Remote Attestation common encodings:
https://datatracker.ietf.org/doc/html/draft-richardson-rats-usecases-08
