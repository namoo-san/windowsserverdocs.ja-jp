# [Windows Server 2016 のパフォーマンス チューニング ガイドライン](index.md)
## [サーバー ハードウェアのチューニング](hardware/index.md)
### [パフォーマンスに関する考慮事項](hardware/index.md)
### [電源に関する考慮事項](hardware/power.md)
#### [電源とパフォーマンスのチューニング](hardware/power/power-performance-tuning.md)
#### [プロセッサの電源管理 (PPM) のチューニング](hardware/power/processor-power-management-tuning.md)
#### [推奨されるバランスの電源プラン パラメーター](hardware/power/recommended-balanced-plan-parameters.md)
## サーバーの役割のチューニング
### [Active Directory サーバー](role/active-directory-server/index.md)
#### [AD DS のキャパシティ プランニング](role/active-directory-server/capacity-planning-for-active-directory-domain-services.md)
#### [サイト定義に関する考慮事項](role/active-directory-server/site-definition-considerations.md)
#### [ハードウェアに関する考慮事項](role/active-directory-server/hardware-considerations.md)
#### [メモリ使用量に関する考慮事項](role/active-directory-server/memory-usage-considerations.md)
#### [LDAP に関する考慮事項](role/active-directory-server/ldap-considerations.md)
#### [ADDS パフォーマンスのトラブルシューティング](role/active-directory-server/troubleshoot.md)
### [ファイル サーバー](role/file-server/index.md)
#### [SMB ファイル サーバー](role/file-server/smb-file-server.md)
#### [NFS ファイル サーバー](role/file-server/nfs-file-server.md)
### [Hyper-V Server](role/hyper-v-server/index.md)
#### [用語](role/hyper-v-server/terminology.md)
#### [アーキテクチャ](role/hyper-v-server/architecture.md)
#### [構成](role/hyper-v-server/configuration.md)
#### [プロセッサのパフォーマンス](role/hyper-v-server/processor-performance.md)
#### [メモリのパフォーマンス](role/hyper-v-server/memory-performance.md)
#### [ストレージ I/O のパフォーマンス](role/hyper-v-server/storage-io-performance.md)
#### [ネットワーク I/O のパフォーマンス](role/hyper-v-server/network-io-performance.md)
#### [仮想化環境のボトルネックの検出](role/hyper-v-server/detecting-virtualized-environment-bottlenecks.md)
#### [Linux 仮想マシンに関する考慮事項](role/hyper-v-server/linux-virtual-machine-considerations.md)
### [Windows Server コンテナー](role/windows-server-container/index.md)
### [リモート デスクトップ サービス](role/remote-desktop/session-hosts.md)
#### [セッション ホスト](role/remote-desktop/session-hosts.md)
#### [仮想化ホスト](role/remote-desktop/virtualization-hosts.md)
#### [ゲートウェイ](role/remote-desktop/gateways.md)
### [Web サーバー](role/web-server/index.md)
#### [IIS 10.0 のチューニング](role/web-server/tuning-iis-10.md)
#### [HTTP 1.1/2](role/web-server/http-performance.md)
## サーバー サブシステムのチューニング
### [キャッシュとメモリのチューニング](subsystem/cache-memory-management/index.md)
#### [キャッシュおよびメモリ マネージャーのパフォーマンスのトラブルシューティング](subsystem/cache-memory-management/troubleshoot.md)
#### [キャッシュおよびメモリ マネージャーの機能強化](subsystem/cache-memory-management/improvements-in-windows-server.md)
### [ネットワーク サブシステムのチューニング](../../networking/technologies/network-subsystem/net-sub-performance-top.md)
#### [ネットワーク アダプターを選択する](../../networking/technologies/network-subsystem/net-sub-choose-nic.md)
#### [ネットワーク インターフェイスの順序を構成する](../../networking/technologies/network-subsystem/net-sub-interface-metric.md)
#### [ネットワーク アダプターのチューニング](../../networking/technologies/network-subsystem/net-sub-performance-tuning-nics.md)
#### [ネットワーク関連のパフォーマンス カウンター](../../networking/technologies/network-subsystem/net-sub-performance-counters.md)
#### [ネットワーク ワークロードに関するパフォーマンス ツール](../../networking/technologies/network-subsystem/net-sub-performance-tools.md)
#### [ネットワーク パフォーマンスのための NIC チーミング](../../networking/technologies/nic-teaming/NIC-Teaming.md)
#### [仮想マシン (VM) の NIC チーミング](../../networking/technologies/nic-teaming/nict-vms.md)
#### [NIC チーミングおよび仮想ローカル エリア ネットワーク (VLAN)](../../networking/technologies/nic-teaming/nict-and-vlans.md)
#### [NIC チーミングでの MAC アドレスの使用と管理](../../networking/technologies/nic-teaming/NIC-Teaming-MAC-address-Use-and-Management.md)
#### [ホスト コンピューターまたは VM 上に新しい NIC チームを作成する](../../networking/technologies/nic-teaming/create-a-New-NIC-Team-on-a-Host-computer-or-VM.md)
#### [新しい NIC チームを作成する](../../networking/technologies/nic-teaming/create-a-New-NIC-Team.md)
#### [VM に新しい NIC チームを作成する](../../networking/technologies/nic-teaming/create-a-New-NIC-Team-in-a-VM.md)
#### [NIC チーミングのトラブルシューティング](../../networking/technologies/nic-teaming/Troubleshooting-NIC-Teaming.md)
### [ソフトウェア定義ネットワーク (SDN) のチューニング](subsystem/software-defined-networking/index.md)
#### [HNV ゲートウェイのパフォーマンス](subsystem/software-defined-networking/hnv-gateway-performance.md)
#### [SLB ゲートウェイのパフォーマンス](subsystem/software-defined-networking/slb-gateway-performance.md)
### 記憶域サブシステムのチューニング
#### [記憶域スペース ダイレクトのチューニング](subsystem/storage-spaces-direct/index.md)
#### [記憶域レプリケーションの FAQ](../../storage/storage-replica/storage-replica-frequently-asked-questions.md)
#### [データ重複除去の高度な設定](../../storage/data-deduplication/advanced-settings.md)
## [PowerShell のチューニング](powershell/index.md)
### [スクリプト作成に関する考慮事項](powershell/script-authoring-considerations.md)
### [モジュール作成に関する考慮事項](powershell/module-authoring-considerations.md)
## [チューニングに関するその他のリソース](additional-resources.md)
