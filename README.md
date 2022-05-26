# Tendermint

![banner](docs/tendermint-core-image.jpg)

[Byzantine-Fault Tolerant](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance)
[State Machines](https://en.wikipedia.org/wiki/State_machine_replication).
Or [Blockchain](<https://en.wikipedia.org/wiki/Blockchain_(database)>), for short.

[![version](https://img.shields.io/github/tag/tendermint/tendermint.svg)](https://github.com/tendermint/tendermint/releases/latest)
[![API Reference](https://camo.githubusercontent.com/915b7be44ada53c290eb157634330494ebe3e30a/68747470733a2f2f676f646f632e6f72672f6769746875622e636f6d2f676f6c616e672f6764646f3f7374617475732e737667)](https://pkg.go.dev/github.com/tendermint/tendermint)
[![Go version](https://img.shields.io/badge/go-1.15-blue.svg)](https://github.com/moovweb/gvm)
[![Discord chat](https://img.shields.io/discord/669268347736686612.svg)](https://discord.gg/AzefAFd)
[![license](https://img.shields.io/github/license/tendermint/tendermint.svg)](https://github.com/tendermint/tendermint/blob/master/LICENSE)
[![tendermint/tendermint](https://tokei.rs/b1/github/tendermint/tendermint?category=lines)](https://github.com/tendermint/tendermint)
[![Sourcegraph](https://sourcegraph.com/github.com/tendermint/tendermint/-/badge.svg)](https://sourcegraph.com/github.com/tendermint/tendermint?badge)

| Branch | Tests                                                                                                                                                                                                                                                  | Coverage                                                                                                                             | Linting                                                                    |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------- |
| master | [![CircleCI](https://circleci.com/gh/tendermint/tendermint/tree/master.svg?style=shield)](https://circleci.com/gh/tendermint/tendermint/tree/master) </br> ![Tests](https://github.com/tendermint/tendermint/workflows/Tests/badge.svg?branch=master) | [![codecov](https://codecov.io/gh/tendermint/tendermint/branch/master/graph/badge.svg)](https://codecov.io/gh/tendermint/tendermint) | ![Lint](https://github.com/tendermint/tendermint/workflows/Lint/badge.svg) |

Tendermint Core, herhangi bir programlama dilinde yazılmış bir durum geçiş makinesi alan Bizans Hata Toleranslı (BFT) ara yazılımıdır -
ve birçok makinede güvenli bir şekilde çoğaltır.

Protokol ayrıntıları için bkz. [the specification](https://github.com/tendermint/spec).

Güvenlik ve canlılık kanıtları dahil olmak üzere fikir birliği protokolünün ayrıntılı analizi için,
son makalemize bakın, "[The latest gossip on BFT consensus](https://arxiv.org/abs/1807.04938)".

## Releases

Lütfen üretim dalınız olarak master'a güvenmeyin. Use [releases](https://github.com/tendermint/tendermint/releases) instead.

Tendermint, hem özel hem de kamusal ortamlarda üretimde kullanılıyor,
en önemlisi blok zincirleri [Cosmos Network](https://cosmos.network/).
Ancak, protokolde ve API'lerde hala önemli değişiklikler yapıyoruz ve henüz v1.0'ı yayınlamadık.
Kullanım hakkında daha fazla bilgi için aşağıya bakın [versioning](#versioning).

Her durumda, Tendermint'i üretimde çalıştırmayı düşünüyorsanız, size yardımcı olmaktan memnuniyet duyarız.. İletişime geçmek için bu adresleri 
kullanın.[over email](mailto:hello@interchain.berlin) ya da [sohbete katılın](https://discord.gg/AzefAFd).

## Güvenlik

Bir güvenlik açığını bildirmek için, bu proglara bakabilirsiniz [bug bounty
program](https://hackerone.com/tendermint). 
Aradığımız hata türlerinin örnekleri için, buraya göz atın [our security policy](SECURITY.md)

Ayrıca güvenlik güncellemeleri için özel bir posta listesi tutuyoruz. Sadece bu posta listesini kullanacağız
Tendermint Core'daki güvenlik açıklarını ve düzeltmeleri size bildirmek için. Abone olabilirsiniz [here](http://eepurl.com/gZ5hQD).

##Minimum Gereksinimler

| Gereklilik  |   Notlar        |
| ----------- | ---------------- |
| Go version  | Go1.15 or higher |

## Belgeler

Eksiksiz belgeler adresinde bulunabilir. [website](https://docs.tendermint.com/master/).

### Yükleme

See the [install instructions](/docs/introduction/install.md).

### Hızlı Başlangıç

- [Tek node](/docs/introduction/quick-start.md)
- [Local cluster using docker-compose](/docs/networks/docker-compose.md)
- [Remote cluster using Terraform and Ansible](/docs/networks/terraform-and-ansible.md)
- [Join the Cosmos testnet](https://cosmos.network/testnet)

## Contributing

lütfen riayet ediniz [Code of Conduct](CODE_OF_CONDUCT.md) tüm etkileşimlerde.

Projeye katkıda bulunmadan önce, lütfen bir göz atın [contributing guidelines](CONTRIBUTING.md)
ve [style guide](STYLE_GUIDE.md). Şunu da okumanız faydalı olabilir.
[specifications](https://github.com/tendermint/spec), izleyin [Developer Sessions](/docs/DEV_SESSIONS.md), 
ve kendinizi tanıyın
[Architectural Decision Records](https://github.com/tendermint/tendermint/tree/master/docs/architecture).

## Sürüm oluşturma

### Semantik Sürüm Oluşturma

Tendermint kullanımı [Semantic Versioning](http://semver.org/) sürümün ne zaman ve nasıl değişeceğini belirlemek için.
SemVer'e göre, genel API'deki herhangi bir şey 1.0.0 sürümünden önce herhangi bir zamanda değişebilir.

Bu 0.X.X günlerinde Tendermint kullanıcılarına biraz istikrar sağlamak için MINOR sürümü kullanılıyor
toplam genel API'nin bir alt kümesindeki son değişiklikleri bildirmek için. Bu alt küme, tüm
diğer işlemlere (cli, rpc, p2p, vb.) maruz kalan ancak
Go API'lerini içerir.

Bununla birlikte, aşağıdaki paketlerdeki kırılma değişiklikleri,
CHANGELOG, KÜÇÜK sürüm darbelerine yol açmasalar bile:

- crypto
- config
- libs
    - bech32
    - bits
    - bytes
    - json
    - log
    - math
    - net
    - os
    - protoio
    - rand
    - sync
    - strings
    - service
- node
- rpc/client
- types

### Yükseltmeler

1.0.0 öncesi teknik borç birikiminden kaçınmak amacıyla,
değişikliklerin (yani MINOR sürümündeki tümseklerin) bozulacağını garanti etmiyoruz.
mevcut Tendermint blok zincirleriyle çalışacak. Bu durumlarda yapacaksın
yeni bir blok zinciri başlatmanız veya eskisini elde etmek için özel bir şeyler yazmanız gerekir.
verileri yeni zincire aktarın. Ancak, PATCH sürümündeki herhangi bir tümsek,
mevcut blok zinciri geçmişleriyle uyumlu.


Yükseltme hakkında daha fazla bilgi için, bakınız [UPGRADING.md](./UPGRADING.md).

### Desteklenen Sürümler

Küçük bir çekirdek ekip olduğumuz için, güvenlik güncellemeleri de dahil olmak üzere yalnızca yama güncellemelerini gönderiyoruz,
en son küçük sürüme ve en son ikinci küçük sürüme. Sonuç olarak,
Tendermint'i güncel tutmanızı şiddetle tavsiye ederiz. Yükseltme talimatları bulunabilir
 [UPGRADING.md](./UPGRADING.md).

## Kaynaklar

### Tendermint çekirdeği

Blok zinciri veri yapıları ve p2p protokolleri hakkında ayrıntılar için, bakınız
[Tendermint specification](https://docs.tendermint.com/master/spec/).

Yazılımı kullanmayla ilgili ayrıntılar için, buuraya bakınız [documentation](/docs/) aynı zamanda 
ev sahipliği yapan: <https://docs.tendermint.com/master/>

### Araçlar

Kıyaslama şu şekilde sağlanır: [`tm-load-test`](https://github.com/informalsystems/tm-load-test).
Ek araçlar şurada bulunabilir [/docs/tools](/docs/tools).

### Uygulamalar

- [Cosmos SDK](http://github.com/cosmos/cosmos-sdk); a cryptocurrency application framework
- [Ethermint](http://github.com/cosmos/ethermint); Ethereum on Tendermint
- [Many more](https://tendermint.com/ecosystem)

### Araştırmalar

- [The latest gossip on BFT consensus](https://arxiv.org/abs/1807.04938)
- [Master's Thesis on Tendermint](https://atrium.lib.uoguelph.ca/xmlui/handle/10214/9769)
- [Original Whitepaper: "Tendermint: Consensus Without Mining"](https://tendermint.com/static/docs/tendermint.pdf)
- [Blog](https://blog.cosmos.network/tendermint/home)
