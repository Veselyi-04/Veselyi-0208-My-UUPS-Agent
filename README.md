# Veselyi-0208-My-UUPS-Agent
Veselyi#0208 My UUPS Agent

This agent detects malicious transactions to the openzeppelin non-ideatised UUPS proxy. (For more information on the vulnerability, see https://forum.openzeppelin.com/t/uupsupgradeable-vulnerability-post-mortem/15680/8)

It is important to distinguish between UUPS Proxy and Transpararent Upgradeable Proxy (since they both emit an Upgradeed event with the same signature) to reduce false positives. Hence, the agent checks for an owner slot that is using the Transpararent Upgradeable proxy, if the slot is empty, it is a UUPS proxy.

The agent reports that both the Upgrade event and the AdminChanged event are raised with a high degree of certainty in one transaction, as there is a very high probability that this is an exploit.

Checking code size 0 will not work, as it does when the exploit transaction is pending, and can lead to ambiguity.
