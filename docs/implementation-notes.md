# Implementation notes

## Azure

- VNet: `otix_VNET`
- Address space: `172.16.0.0/16`
- GatewaySubnet: `172.16.0.0/27`
- Workload subnet: `SERVERS_SUBNET` → `172.16.1.0/24`
- Virtual Network Gateway: `AZURE_VIRTUAL_NETWORK_GW`
- Gateway SKU: `VpnGw1AZ`
- Gateway type: VPN
- VPN type: Route-based
- Local Network Gateway: `FWFGT_LOCAL_NETWORK_GW`
- On-premises address space advertised to Azure: `192.168.5.0/24`
- S2S connection: `S2S_HQ_AZURE`

At the time of capture, the Azure connection showed **Connected** and had transferred approximately **194.64 MiB inbound** and **167.1 MiB outbound**.

## FortiGate

- Tunnel: `S2S_HQ_AZ`
- Interface: `wan1`
- IKE version: 2
- Authentication method: pre-shared key
- Phase 1: AES256 / SHA1 / DH Group 2 / 27000-second lifetime
- Phase 2: AES256 / SHA1 / replay detection enabled / PFS disabled / 27000-second lifetime

## Validation

Validation included:

1. Azure VPN connection status reporting **Connected**.
2. FortiGate IPsec tunnel reporting **Up**.
3. Azure-to-on-premises ICMP traffic to a `192.168.5.x` host.
4. Azure-to-on-premises web access to an internal service.
5. Azure tunnel ingress and egress activity visible on the gateway metrics.

## Production-hardening considerations

This repository documents a lab. For production, validate current Microsoft and Fortinet recommendations for IKE/IPsec algorithms, route design, HA, logging, monitoring, NSGs/firewall rules, key rotation, and redundancy.
