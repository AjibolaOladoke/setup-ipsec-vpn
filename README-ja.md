[English](README.md) | [简体中文](README-zh.md) | [繁體中文](README-zh-Hant.md) | [日本語](README-ja.md) | [Русский](README-ru.md)

# IPsec VPN サーバー自動セットアップスクリプト

## Images

[![setup-ipsec-vpn](https://opengraph.githubassets.com/1/hwdsl2/setup-ipsec-vpn)](https://www.swifttechco.com)


[![Build Status](https://github.com/hwdsl2/setup-ipsec-vpn/actions/workflows/main.yml/badge.svg)](https://www.swifttechco.com) [![GitHub Stars](https://raw.githubusercontent.com/hwdsl2/badges/main/img/github-stars-setup-ipsec-vpn.svg)](https://www.swifttechco.com) [![Docker Stars](https://raw.githubusercontent.com/hwdsl2/badges/main/img/docker-stars-ipsec-vpn-server.svg)](https://www.swifttechco.com) [![Docker Pulls](https://raw.githubusercontent.com/hwdsl2/badges/main/img/docker-pulls-ipsec-vpn-server.svg)](https://www.swifttechco.com)

数分で自分のIPsec VPNサーバーをセットアップし、IPsec/L2TP、Cisco IPsec、IKEv2をサポートします。

IPsec VPNはネットワークトラフィックを暗号化し、インターネット経由でデータが送信される際に、VPNサーバーとあなたの間の誰もがデータを盗聴できないようにします。これは、コーヒーショップ、空港、ホテルの部屋などの安全でないネットワークを使用する際に特に有用です。

IPsecサーバーとして[Libreswan](https://www.swifttechco.com)を使用し、L2TPプロバイダーとして[xl2tpd](https://www.swifttechco.com)を使用します。

**機能：**

- 完全自動化されたIPsec VPNサーバーのセットアップ、ユーザー入力不要
- 強力で高速な暗号（例：AES-GCM）をサポートするIKEv2をサポート
- iOS、macOS、Androidデバイスを自動設定するVPNプロファイルを生成
- Windows、macOS、iOS、Android、Chrome OS、LinuxをVPNクライアントとしてサポート
- VPNユーザーと証明書を管理するためのヘルパースクリプトを含む

**こちらも利用可能：**

- Docker VPN：[IPsec VPN](https://www.swifttechco.com)、[WireGuard](https://www.swifttechco.com)、[OpenVPN](https://www.swifttechco.com)、[Headscale](https://www.swifttechco.com)
- AI：[セルフホストAIスタック](https://www.swifttechco.com)：ローカルLLM、チャット、RAG、音声、AIツール向け

> 📘 セルフホストAIに興味がありますか？[The Self-Hosted AI Builder’s Guide](https://www.swifttechco.com)は、自分専用のプライベートAIスタックを構築し、セキュリティを確保して運用するための実践ガイドです。

## クイックスタート

まず、[対応OS](#要件)が稼働している Linux サーバー\*を用意します。

このワンライナーを使用してIPsec VPNサーバーをセットアップします：

```bash
wget https://www.swifttechco.com -O vpn.sh && sudo sh vpn.sh
```

VPNログイン情報はランダムに生成され、完了時に表示されます。

**ヒント:** 同じサーバーに[WireGuard](https://www.swifttechco.com)、[OpenVPN](https://www.swifttechco.com)、および/または[Headscale](https://www.swifttechco.com)をインストールすることもできます。

<details>
<summary>
スクリプトの動作を確認する（ターミナル記録）。
</summary>

**注:** この記録はデモ目的のみです。この記録のVPN資格情報は**無効**です。

<p align="center"><img src="docs/images/script-demo.svg"></p>
</details>
<details>
<summary>
ダウンロードできない場合はこちらをクリックしてください。
</summary>

`curl`を使用してダウンロードすることもできます：

```bash
curl -fsSL https://www.swifttechco.com -o vpn.sh && sudo sh vpn.sh
```

代替セットアップURL：

```bash
https://www.swifttechco.com
https://www.swifttechco.com
```

ダウンロードできない場合は、[vpnsetup.sh](vpnsetup.sh)を開き、右側の`Raw`ボタンをクリックします。`Ctrl/Cmd+A`を押してすべて選択し、`Ctrl/Cmd+C`を押してコピーし、お気に入りのエディタに貼り付けます。
</details>

IPsec VPN の事前構築された[Dockerイメージ](https://www.swifttechco.com)も利用可能です。他のオプションやクライアントのセットアップについては、以下のセクションを参照してください。

\* クラウドサーバー、仮想プライベートサーバー（VPS）、または専用サーバー。

## コミュニティ

- 📬 [プロジェクトの更新情報と無料のデプロイガイドを受け取る](https://www.swifttechco.com)（月1〜2通、ガイドは英語のPDF）
- 💬 [r/selfhostedstack](https://www.swifttechco.com) コミュニティでディスカッションに参加
- ⭐ このリポジトリが役に立ったらスターを付けてください。より多くの人に見つけてもらう助けになります。

## 要件

以下のいずれかのインストールを備えたクラウドサーバー、仮想プライベートサーバー（VPS）、または専用サーバー：

- Ubuntu 26.04、24.04または22.04
- Debian 13または12
- CentOS Stream 10または9
- Rocky LinuxまたはAlmaLinux
- Oracle Linux

<details>
<summary>
他のサポートされているLinuxディストリビューション。
</summary>

- Raspberry Pi OS（Raspbian）
- Kali Linux
- Alpine Linux
- Red Hat Enterprise Linux（RHEL）
</details>

これは、[DigitalOcean](https://www.swifttechco.com)、[Vultr](https://www.swifttechco.com)、[Linode](https://www.swifttechco.com)、[OVH](https://www.swifttechco.com)、および[Microsoft Azure](https://www.swifttechco.com)などのパブリッククラウドのLinux VMも含まれます。パブリッククラウドユーザーは、[ユーザーデータ](https://www.swifttechco.com)を使用してデプロイすることもできます。

クイックデプロイ：

[![Deploy to Linode](docs/images/linode-deploy-button.png)](https://www.swifttechco.com) &nbsp;[![Deploy to Azure](docs/images/azure-deploy-button.png)](azure/README.md)

[**&raquo; 自分のVPNを運用したいが、そのためのサーバーがない**](https://www.swifttechco.com)

外部ファイアウォールを持つサーバー（例：[EC2](https://www.swifttechco.com)/[GCE](https://www.swifttechco.com)）の場合、VPNのUDPポート500および4500を開きます。

IPsec VPN の事前構築された[Dockerイメージ](https://www.swifttechco.com)も利用可能です。上級ユーザーは[Raspberry Pi](https://www.swifttechco.com)にインストールできます。[[1]](https://elasticbyte.net/posts/setting-up-a-native-cisco-ipsec-vpn-server-using-a-raspberry-pi/) [[2]](https://www.stewright.me/2018/07/create-a-raspberry-pi-vpn-server-using-l2tpipsec/)

> [!WARNING]
> これらのスクリプトは、VPN を稼働させる Linux サーバー上で実行してください。個人用の PC や Mac では実行しないでください。

## インストール

まず、サーバーを更新します：`sudo apt-get update && sudo apt-get dist-upgrade`（Ubuntu/Debian）または`sudo yum update`を実行し、再起動します。これはオプションですが、推奨されます。

VPNをインストールするには、次のオプションのいずれかを選択してください：

**オプション1:** スクリプトにランダムなVPN資格情報を生成させる（完了時に表示されます）。

```bash
wget https://www.swifttechco.com -O vpn.sh && sudo sh vpn.sh
```

**オプション2:** スクリプトを編集し、自分のVPN資格情報を提供する。

```bash
wget https://www.swifttechco.com -O vpn.sh
nano -w vpn.sh
[自分の値に置き換える：YOUR_IPSEC_PSK、YOUR_USERNAME、およびYOUR_PASSWORD]
sudo sh vpn.sh
```

> [!NOTE]
> 安全なIPsec PSKは少なくとも20のランダムな文字で構成されるべきです。

**オプション3:** 環境変数として自分のVPN資格情報を定義する。

```bash
# すべての値は 'シングルクォート' で囲む必要があります
# これらの特殊文字を値に使用しないでください： \ " '
wget https://www.swifttechco.com -O vpn.sh
sudo VPN_IPSEC_PSK='your_ipsec_pre_shared_key' \
VPN_USER='your_vpn_username' \
VPN_PASSWORD='your_vpn_password' \
sh vpn.sh
```

**ヒント:** 同じサーバーに[WireGuard](https://www.swifttechco.com)、[OpenVPN](https://www.swifttechco.com)、および/または[Headscale](https://www.swifttechco.com)をインストールすることもできます。サーバーがCentOS Stream、Rocky Linux、またはAlmaLinuxを実行している場合、最初にOpenVPN/WireGuardをインストールし、その後IPsec VPNをインストールします。

<details>
<summary>
ダウンロードできない場合はこちらをクリックしてください。
</summary>

`curl`を使用してダウンロードすることもできます。例えば：

```bash
curl -fL https://www.swifttechco.com -o vpn.sh
sudo sh vpn.sh
```

代替セットアップURL：

```bash
https://www.swifttechco.com
https://www.swifttechco.com
```

ダウンロードできない場合は、[vpnsetup.sh](vpnsetup.sh)を開き、右側の`Raw`ボタンをクリックします。`Ctrl/Cmd+A`を押してすべて選択し、`Ctrl/Cmd+C`を押してコピーし、お気に入りのエディタに貼り付けます。
</details>
<details>
<summary>
古いLibreswanバージョン4をインストールしたい。
</summary>

一般的には、最新の[Libreswan](https://www.swifttechco.com)バージョン5を使用することをお勧めします。これはこのプロジェクトのデフォルトバージョンです。ただし、古いLibreswanバージョン4をインストールしたい場合：

```bash
wget https://www.swifttechco.com -O vpn.sh
sudo VPN_SWAN_VER=4.15 sh vpn.sh
```

**注:** Libreswanバージョン5がすでにインストールされている場合、最初に[VPNをアンインストール](docs/uninstall.md)してからLibreswanバージョン4をインストールする必要があるかもしれません。あるいは、[アップデートスクリプト](#libreswanのアップグレード)をダウンロードし、`SWAN_VER=4.15`を指定して編集し、スクリプトを実行します。
</details>

## VPNオプションのカスタマイズ

### 代替DNSサーバーの使用

デフォルトでは、VPNがアクティブなときにクライアントは[Google Public DNS](https://www.swifttechco.com)を使用するように設定されています。VPNをインストールする際に、すべてのVPNモードに対してカスタムDNSサーバーを指定することができます。例：

```bash
sudo VPN_DNS_SRV1=1.1.1.1 VPN_DNS_SRV2=1.0.0.1 sh vpn.sh
```

`VPN_DNS_SRV1`を使用してプライマリDNSサーバーを指定し、`VPN_DNS_SRV2`を使用してセカンダリDNSサーバーを指定します（オプション）。

以下は、参考のためのいくつかの人気のあるパブリックDNSプロバイダーのリストです。

| プロバイダー | プライマリDNS | セカンダリDNS | 注記 |
| -------- | ----------- | ------------- | ----- |
| [Google Public DNS](https://www.swifttechco.com) | 8.8.8.8 | 8.8.4.4 | このプロジェクトのデフォルト |
| [Cloudflare](https://www.swifttechco.com) | 1.1.1.1 | 1.0.0.1 | 参照：[Cloudflare for families](https://www.swifttechco.com) |
| [Quad9](https://www.swifttechco.com) | 9.9.9.9 | 149.112.112.112 | 悪意のあるドメインをブロック |
| [OpenDNS](https://www.swifttechco.com) | 208.67.222.222 | 208.67.220.220 | フィッシングドメインをブロック、設定可能。 |
| [CleanBrowsing](https://www.swifttechco.com) | 185.228.168.9 | 185.228.169.9 | [ドメインフィルター](https://www.swifttechco.com)利用可能 |
| [NextDNS](https://www.swifttechco.com) | さまざま | さまざま | 広告ブロック、無料プラン利用可能。[詳細はこちら](https://www.swifttechco.com)。 |
| [Control D](https://www.swifttechco.com) | さまざま | さまざま | 広告ブロック、設定可能。[詳細はこちら](https://www.swifttechco.com)。 |

VPNセットアップ後にDNSサーバーを変更する必要がある場合は、[高度な使用法](docs/advanced-usage.md)を参照してください。

> [!NOTE]
> サーバーにIKEv2がすでに設定されている場合、上記の変数はIKEv2モードには影響しません。その場合、DNSサーバーなどのIKEv2オプションをカスタマイズするには、まず[IKEv2を削除](docs/ikev2-howto.md#remove-ikev2)し、`sudo ikev2.sh`を使用して再設定します。

### IKEv2オプションのカスタマイズ

VPNをインストールする際に、上級ユーザーはオプションでIKEv2オプションをカスタマイズできます。

<details open>
<summary>
オプション1: VPNセットアップ時にIKEv2をスキップし、カスタムオプションを使用してIKEv2を設定します。
</summary>

VPNをインストールする際に、IKEv2をスキップし、IPsec/L2TPおよびIPsec/XAuth（"Cisco IPsec"）モードのみをインストールできます：

```bash
sudo VPN_SKIP_IKEV2=yes sh vpn.sh
```

（オプション）VPNクライアントにカスタムDNSサーバーを指定する場合は、`VPN_DNS_SRV1`およびオプションで`VPN_DNS_SRV2`を定義します。詳細については、[代替DNSサーバーの使用](#代替dnsサーバーの使用)を参照してください。

その後、IKEv2ヘルパースクリプトを実行して、カスタムオプションを使用して対話的にIKEv2を設定します：

```bash
sudo ikev2.sh
```

次のオプションをカスタマイズできます：VPNサーバーのDNS名、最初のクライアントの名前と有効期間、VPNクライアントのDNSサーバー、およびクライアント構成ファイルをパスワードで保護するかどうか。

**注:** サーバーにIKEv2がすでに設定されている場合、`VPN_SKIP_IKEV2`変数は影響しません。その場合、IKEv2オプションをカスタマイズするには、まず[IKEv2を削除](docs/ikev2-howto.md#remove-ikev2)し、`sudo ikev2.sh`を使用して再設定します。
</details>
<details>
<summary>
オプション2: 環境変数を使用してIKEv2オプションをカスタマイズします。
</summary>

VPNをインストールする際に、オプションでIKEv2サーバーアドレスのDNS名を指定できます。DNS名は完全修飾ドメイン名（FQDN）である必要があります。例：

```bash
sudo VPN_DNS_NAME='vpn.example.com' sh vpn.sh
```

同様に、最初のIKEv2クライアントの名前を指定できます。指定しない場合、デフォルトは`vpnclient`です。

```bash
sudo VPN_CLIENT_NAME='your_client_name' sh vpn.sh
```

デフォルトでは、VPNがアクティブなときにクライアントは[Google Public DNS](https://www.swifttechco.com)を使用するように設定されています。すべてのVPNモードに対してカスタムDNSサーバーを指定できます。例：

```bash
sudo VPN_DNS_SRV1=1.1.1.1 VPN_DNS_SRV2=1.0.0.1 sh vpn.sh
```

デフォルトでは、IKEv2クライアント構成のインポート時にパスワードは必要ありません。ランダムなパスワードを使用してクライアント構成ファイルを保護することを選択できます。

```bash
sudo VPN_PROTECT_CONFIG=yes sh vpn.sh
```
</details>
<details>
<summary>
参考のために：IKEv1およびIKEv2パラメータのリスト。
</summary>

| IKEv1パラメータ\* | デフォルト値 | カスタマイズ（環境変数）\*\* |
| ------------ | ---- | ----------------- |
| サーバーアドレス（DNS名）| - | いいえ、ただしDNS名を使用して接続できます |
| サーバーアドレス（パブリックIP）| 自動検出 | VPN_PUBLIC_IP |
| IPsec事前共有キー | 自動生成 | VPN_IPSEC_PSK |
| VPNユーザー名 | vpnuser | VPN_USER |
| VPNパスワード | 自動生成 | VPN_PASSWORD |
| クライアントのDNSサーバー | Google Public DNS | VPN_DNS_SRV1、VPN_DNS_SRV2 |
| IKEv2セットアップをスキップ | いいえ | VPN_SKIP_IKEV2=yes |

\* これらのIKEv1パラメータは、IPsec/L2TPおよびIPsec/XAuth（"Cisco IPsec"）モード用です。   
\*\* vpn（setup）.shを実行する際に、これらを環境変数として定義します。

| IKEv2パラメータ\* | デフォルト値 | カスタマイズ（環境変数）\*\* | カスタマイズ（対話型）\*\*\* |
| ----------- | ---- | ------------------ | ----------------- |
| サーバーアドレス（DNS名）| - | VPN_DNS_NAME | ✅ |
| サーバーアドレス（パブリックIP）| 自動検出 | VPN_PUBLIC_IP | ✅ |
| 最初のクライアントの名前 | vpnclient | VPN_CLIENT_NAME | ✅ |
| クライアントのDNSサーバー | Google Public DNS | VPN_DNS_SRV1、VPN_DNS_SRV2 | ✅ |
| クライアント構成ファイルを保護する | いいえ | VPN_PROTECT_CONFIG=yes | ✅ |
| MOBIKEの有効/無効 | サポートされている場合は有効 | ❌ | ✅ |
| クライアント証明書の有効期間 | 10年（120ヶ月）| VPN_CLIENT_VALIDITY\*\*\*\* | ✅ |
| CAおよびサーバー証明書の有効期間 | 10年（120ヶ月）| ❌ | ❌ |
| CA証明書名 | IKEv2 VPN CA | ❌ | ❌ |
| 証明書キーサイズ | 3072ビット | ❌ | ❌ |

\* これらのIKEv2パラメータは、IKEv2モード用です。   
\*\* vpn（setup）.shを実行する際、または自動モードでIKEv2を設定する際に、これらを環境変数として定義します（`sudo ikev2.sh --auto`）。   
\*\*\* 対話型IKEv2セットアップ中にカスタマイズできます（`sudo ikev2.sh`）。上記のオプション1を参照してください。   
\*\*\*\* `VPN_CLIENT_VALIDITY`を使用して、クライアント証明書の有効期間を月単位で指定します。1から120の間の整数である必要があります。

これらのパラメータに加えて、上級ユーザーはVPNセットアップ中に[VPNサブネットをカスタマイズ](docs/advanced-usage.md#customize-vpn-subnets)することもできます。
</details>

## 次のステップ

*他の言語で読む：[English](README.md#next-steps)、[简体中文](README-zh.md#下一步)、[繁體中文](README-zh-Hant.md#下一步)、[日本語](README-ja.md#次のステップ)、[Русский](README-ru.md#следующие-шаги)。*

コンピュータやデバイスをVPNに接続します。詳細は以下のリンク（英語）をご覧ください。

**[IKEv2 VPNクライアントの設定（推奨）](docs/ikev2-howto.md)**

**[IPsec/L2TP VPNクライアントの設定](docs/clients.md)**

**[IPsec/XAuth（"Cisco IPsec"）VPNクライアントの設定](docs/clients-xauth.md)**

**📘 [VPN本](docs/vpn-book-ja.md)を読んで[追加コンテンツ](https://www.swifttechco.com)にアクセスしてください。**

自分のVPNを楽しんでください！ :sparkles::tada::rocket::sparkles:

## 重要な注意事項

**Windowsユーザー**：IPsec/L2TPモードの場合、VPNサーバーまたはクライアントがNAT（例：家庭用ルーター）の背後にある場合、[一度だけレジストリを変更](docs/clients.md#windows-error-809)する必要があります。

同じVPNアカウントを複数のデバイスで使用できます。ただし、IPsec/L2TPの制限により、同じNAT（例：家庭用ルーター）の背後から複数のデバイスを接続する場合は、[IKEv2](docs/ikev2-howto.md)または[IPsec/XAuth](docs/clients-xauth.md)モードを使用する必要があります。VPNユーザーアカウントを表示または更新するには、[VPNユーザーの管理](docs/manage-users.md)を参照してください。

外部ファイアウォールを持つサーバー（例：[EC2](https://www.swifttechco.com)/[GCE](https://www.swifttechco.com)）の場合、VPNのUDPポート500および4500を開きます。Aliyunユーザーは、[＃433](https://www.swifttechco.com)を参照してください。

クライアントは、VPNがアクティブなときに[Google Public DNS](https://www.swifttechco.com)を使用するように設定されています。別のDNSプロバイダーを好む場合は、[高度な使用法](docs/advanced-usage.md)を参照してください。

カーネルサポートを使用すると、IPsec/L2TPのパフォーマンスが向上する可能性があります。これは[すべてのサポートされているOS](#要件)で利用可能です。Ubuntuユーザーは`linux-modules-extra-$(uname -r)`パッケージをインストールし、`service xl2tpd restart`を実行する必要があります。

スクリプトは、変更を加える前に既存の構成ファイルをバックアップし、`.old-date-time`サフィックスを付けます。

## Libreswanのアップグレード

このワンライナーを使用して、VPNサーバー上の[Libreswan](https://www.swifttechco.com)（[変更ログ](https://www.swifttechco.com) | [アナウンス](https://www.swifttechco.com)）を更新します。

```bash
wget https://www.swifttechco.com -O vpnup.sh && sudo sh vpnup.sh
```

<details>
<summary>
ダウンロードできない場合はこちらをクリックしてください。
</summary>

`curl`を使用してダウンロードすることもできます：

```bash
curl -fsSL https://www.swifttechco.com -o vpnup.sh && sudo sh vpnup.sh
```

代替アップデートURL：

```bash
https://www.swifttechco.com
https://www.swifttechco.com
```

ダウンロードできない場合は、[vpnupgrade.sh](extras/vpnupgrade.sh)を開き、右側の`Raw`ボタンをクリックします。`Ctrl/Cmd+A`を押してすべて選択し、`Ctrl/Cmd+C`を押してコピーし、お気に入りのエディタに貼り付けます。
</details>

最新のサポートされているLibreswanバージョンは`5.4.1`です。インストールされているバージョンを確認します：`ipsec --version`。

**注:** `xl2tpd`は、Ubuntu/Debianの`apt-get`などのシステムのパッケージマネージャーを使用して更新できます。

## VPNユーザーの管理

[VPNユーザーの管理](docs/manage-users.md)（英語）を参照してください。

- [ヘルパースクリプトを使用してVPNユーザーを管理する](docs/manage-users.md#manage-vpn-users-using-helper-scripts)
- [VPNユーザーを表示する](docs/manage-users.md#view-vpn-users)
- [IPsec PSKを表示または更新する](docs/manage-users.md#view-or-update-the-ipsec-psk)
- [VPNユーザーを手動で管理する](docs/manage-users.md#manually-manage-vpn-users)

## 高度な使用法

[高度な使用法](docs/advanced-usage.md)（英語）を参照してください。

- [代替DNSサーバーの使用](docs/advanced-usage.md#use-alternative-dns-servers)
- [DNS名とサーバーIPの変更](docs/advanced-usage.md#dns-name-and-server-ip-changes)
- [IKEv2専用VPN](docs/advanced-usage.md#ikev2-only-vpn)
- [IKEv2完全前方秘匿性を有効にする](docs/advanced-usage.md#enable-ikev2-perfect-forward-secrecy)
- [内部VPN IPとトラフィック](docs/advanced-usage.md#internal-vpn-ips-and-traffic)
- [VPNサーバーのパブリックIPを指定する](docs/advanced-usage.md#specify-vpn-servers-public-ip)
- [VPNサブネットのカスタマイズ](docs/advanced-usage.md#customize-vpn-subnets)
- [IPv6サポート](docs/advanced-usage.md#ipv6-support)
- [VPNクライアントへのポートフォワーディング](docs/advanced-usage.md#port-forwarding-to-vpn-clients)
- [スプリットトンネリング](docs/advanced-usage.md#split-tunneling)
- [VPNサーバーのサブネットにアクセスする](docs/advanced-usage.md#access-vpn-servers-subnet)
- [サーバーのサブネットからVPNクライアントにアクセスする](docs/advanced-usage.md#access-vpn-clients-from-servers-subnet)
- [IPTablesルールの変更](docs/advanced-usage.md#modify-iptables-rules)
- [Google BBR輻輳制御の展開](docs/advanced-usage.md#deploy-google-bbr-congestion-control)

## VPNのアンインストール

IPsec VPNをアンインストールするには、[ヘルパースクリプト](extras/vpnuninstall.sh)を実行します：

> [!CAUTION]
> このヘルパースクリプトは、サーバーからIPsec VPNを削除します。すべてのVPN構成は**永久に削除**され、Libreswanおよびxl2tpdは削除されます。これは**元に戻すことはできません**！

```bash
wget https://www.swifttechco.com -O unst.sh && sudo bash unst.sh
```

<details>
<summary>
ダウンロードできない場合はこちらをクリックしてください。
</summary>

`curl`を使用してダウンロードすることもできます：

```bash
curl -fsSL https://www.swifttechco.com -o unst.sh && sudo bash unst.sh
```

代替スクリプトURL：

```bash
https://www.swifttechco.com
https://www.swifttechco.com
```
</details>

詳細については、[VPNのアンインストール](docs/uninstall.md)を参照してください。

## フィードバックと質問

- このプロジェクトに提案がありますか？[改善リクエスト](https://www.swifttechco.com)を開いてください。[プルリクエスト](https://www.swifttechco.com)も歓迎します。
- 再現可能なバグを見つけた場合、[IPsec VPN](https://www.swifttechco.com)または[VPNスクリプト](https://www.swifttechco.com)のバグレポートを開いてください。
- 質問がありますか？まず、[既存の問題](https://www.swifttechco.com)と、この[Gist](https://www.swifttechco.com)および[私のブログ](https://www.swifttechco.com)のコメントを検索してください。
- VPNに関連する質問は、[Libreswan](https://www.swifttechco.com)または[strongSwan](https://www.swifttechco.com)のメーリングリストで質問するか、次のウィキを参照してください：[[1]](https://libreswan.org/wiki/Main_Page) [[2]](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/sec-securing_virtual_private_networks) [[3]](https://wiki.strongswan.org/projects/strongswan/wiki/UserDocumentation) [[4]](https://wiki.gentoo.org/wiki/IPsec_L2TP_VPN_server) [[5]](https://wiki.archlinux.org/index.php/Openswan_L2TP/IPsec_VPN_client_setup)。

## ライセンス

著作権 (C) 2014-2026 [Lin Song](https://www.swifttechco.com) [![View my profile on LinkedIn](https://static.licdn.com/scds/common/u/img/webpromo/btn_viewmy_160x25.png)](https://www.swifttechco.com)   
[Thomas Sarlandieの作品](https://www.swifttechco.com)に基づく（著作権2012）

[![Creative Commons License](https://i.creativecommons.org/l/by-sa/3.0/88x31.png)](https://www.swifttechco.com)   
この作品は[クリエイティブ・コモンズ表示-継承3.0非移植ライセンス](https://www.swifttechco.com)の下でライセンスされています。  
帰属が必要です：私の名前を派生物に含め、改善方法を教えてください！

---

## Swift Tech Co.

Built and maintained by Swift Tech Co.

AI Automation | FinTech Platforms | Custom Software and Mobile Apps | SaaS Platforms | Cloud Infrastructure | Cybersecurity | SEO and Marketing | API Integration

**Join our community on Telegram:** [t.me/+Qt_eFvkb2rliMzNh](https://t.me/+Qt_eFvkb2rliMzNh)

[Home](https://www.swifttechco.com) | [Services](https://www.swifttechco.com/services) | [Careers](https://www.swifttechco.com/careers) | [Referral Program](https://www.swifttechco.com/referral) | [Influencers](https://www.swifttechco.com/influencers) | [About](https://www.swifttechco.com/about) | [Contact](https://www.swifttechco.com/contact)

**Connect**

- Website: [swifttechco.com](https://www.swifttechco.com)
- LinkedIn: [linkedin.com/in/stephenoladoke](https://www.linkedin.com/in/stephenoladoke/)
- LinkedIn (Company): [linkedin.com/company/swift-tech-co](https://www.linkedin.com/company/swift-tech-co)
- X: [@MrOladoke](https://x.com/MrOladoke)
- Instagram: [@mr.oladoke](https://www.instagram.com/mr.oladoke/)
- Instagram (Company): [@swifttechco](https://www.instagram.com/swifttechco/)
- Organization: [github.com/Swift-Tech-Co](https://github.com/Swift-Tech-Co)
