---
title: VsPackage Registro | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703929"
---
# <a name="vspackage-registration"></a>Registro do VSPackage
VsPacotes devem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] avisar que estão instalados e devem ser carregados. Esse processo é realizado através da redação de informações no registro. Esse é um trabalho típico de um instalador.

> [!NOTE]
> É uma prática aceita durante o desenvolvimento do VSPackage para usar o auto-registro. No [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] entanto, os parceiros não podem enviar seus produtos usando o auto-registro como parte da configuração.

 As entradas de registro em um pacote do Instalador do Windows são geralmente feitas na tabela Registro. Você também pode registrar extensões de arquivo na tabela Registro. No entanto, o Windows Installer fornece suporte integrado através do identificador programático (ProgId), tabelas de classe, extensão e verbo. Para obter mais informações, consulte [Tabelas de banco de dados](/windows/desktop/Msi/database-tables).

 Certifique-se de que suas entradas de registro estão associadas ao componente apropriado para sua estratégia escolhida lado a lado. Por exemplo, as entradas de registro de um arquivo compartilhado devem ser associadas ao componente Windows Installer desse arquivo. Da mesma forma, as entradas de registro de um arquivo específico da versão devem ser associadas ao componente desse arquivo. Caso contrário, instalar ou desinstalar seu VSPackage para uma versão pode [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] quebrar seu VSPackage em outras versões. Para obter mais informações, consulte [Suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> A maneira mais fácil de gerenciar o registro é usar os mesmos dados nos mesmos arquivos tanto para registro de desenvolvedor quanto para registro de tempo de instalação. Por exemplo, algumas ferramentas de desenvolvimento de instalador podem consumir arquivo em formato .reg no tempo de compilação. Se os desenvolvedores mantiverem arquivos .reg para seu próprio desenvolvimento e depuração diários, esses mesmos arquivos poderão ser incluídos no instalador automaticamente. Se você não puder compartilhar automaticamente dados de registro, você deve garantir que a cópia dos dados cadastrais do instalador esteja atualizada.

## <a name="registering-unmanaged-vspackages"></a>Registrando pacotes VS não gerenciados
 Os VSPackages não gerenciados (incluindo os gerados pelo Visual Studio Package Template) usam arquivos .rgs no estilo ATL para armazenar informações de registro. O formato de arquivo .rgs é específico do ATL e geralmente não pode ser consumido como está por uma ferramenta de autoria de instalação. As informações de registro do instalador VSPackage devem ser mantidas separadamente. Por exemplo, os desenvolvedores podem manter arquivos no formato .reg em sincronia com alterações de arquivo .rgs. Os arquivos .reg podem ser mesclados com o RegEdit para trabalho de desenvolvimento ou consumidos por um instalador.

## <a name="registering-managed-vspackages"></a>Registrando pacotes VS gerenciados
 A ferramenta RegPkg lê os atributos de registro de um VSPackage gerenciado e pode escrever as informações diretamente no registro ou gravar arquivos em formato .reg que podem ser consumidos por um instalador.

> [!NOTE]
> A ferramenta RegPkg não é reditribuível e não pode ser usada para registrar um VSPackage no sistema de um usuário.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Por que os pacotes VS não devem se registrar no momento da instalação
 Os instaladores DO VSPackage não devem confiar no auto-registro. À primeira vista, manter os valores de registro de um VSPackage apenas no VSPackage em si parece uma boa ideia. Dado que os desenvolvedores precisam dos valores de registro disponíveis para seu trabalho de rotina e testes, faz sentido evitar manter uma cópia separada dos dados de registro no instalador. O instalador pode contar com o próprio VSPackage para gravar valores de registro.

 Embora bom em teoria, o auto-registro tem várias falhas que o tornam inadequado para a instalação do VSPackage:

- O suporte correto à instalação, desinstalação, reversão de instalação e reversão de desinstalação exige que você seja autor de quatro ações personalizadas para cada VSPackage gerenciado que se auto-registra chamando de RegPkg.

- Sua abordagem ao suporte lado a lado pode exigir que você autorize quatro ações personalizadas que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]invocam RegSvr32 ou RegPkg para cada versão suportada de .

- Uma instalação com módulos auto-registrados não pode ser revertida com segurança porque não há como dizer se as chaves auto-registradas são usadas por outro recurso ou aplicativo.

- DLLs auto-registrados às vezes se ligam a DLLs auxiliares que não estão presentes ou são a versão errada. Em contraste, o Windows Installer pode registrar DLLs usando as tabelas de registro sem dependência do estado atual do sistema.

- O código de auto-registro pode ser negado acesso aos recursos da rede, como bibliotecas de tipo, se um componente for especificado como run-from-source e estiver listado na tabela SelfReg. Isso pode fazer com que a instalação do componente falhe durante uma instalação administrativa.

## <a name="see-also"></a>Confira também
- [Instalador do Windows](/windows/desktop/Msi/windows-installer-portal)
- [Registro gerenciado do pacote](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
