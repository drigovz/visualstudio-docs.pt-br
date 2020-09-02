---
title: Registro de VSPackage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a11f05edb4e7d476fdbcab82d365f9327dd4869a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685279"
---
# <a name="vspackage-registration"></a>Registro do VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

VSPackages deve informar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] que eles estão instalados e devem ser carregados. Esse processo é realizado com a gravação de informações no registro. Esse é um trabalho típico de um instalador.  
  
> [!NOTE]
> É uma prática aceita durante o desenvolvimento do VSPackage para usar o auto-registro. No entanto, [!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)] os parceiros não podem enviar seus produtos usando o auto-registro como parte da instalação.  
  
 As entradas de registro em um pacote de Windows Installer são geralmente feitas na tabela de registro. Você também pode registrar extensões de arquivo na tabela do registro. No entanto, o Windows Installer fornece suporte interno por meio do identificador programático (ProgId), classe, extensão e tabelas de verbos. Para obter mais informações, consulte [tabelas de banco de dados](https://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Verifique se as entradas do registro estão associadas ao componente apropriado para sua estratégia lado a lado escolhida. Por exemplo, as entradas do registro para um arquivo compartilhado devem ser associadas ao componente Windows Installer do arquivo. Da mesma forma, as entradas do registro para um arquivo específico da versão devem ser associadas ao componente desse arquivo. Caso contrário, instalar ou desinstalar seu VSPackage para uma versão do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] pode interromper seu VSPackage em outras versões. Para obter mais informações, consulte [dando suporte a várias versões do Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)  
  
> [!NOTE]
> A maneira mais fácil de gerenciar o registro é usar os mesmos dados nos mesmos arquivos para o registro do desenvolvedor e o registro de tempo de instalação. Por exemplo, algumas ferramentas de desenvolvimento de instalador podem consumir arquivo no formato. reg no momento da compilação. Se os desenvolvedores mantiverem arquivos. reg para seu próprio desenvolvimento diário e depuração, esses mesmos arquivos poderão ser incluídos no instalador automaticamente. Se você não puder compartilhar automaticamente os dados de registro, deverá garantir que a cópia dos dados de registro do instalador seja atual.  
  
## <a name="registering-unmanaged-vspackages"></a>Registrando VSPackages não gerenciados  
 Os VSPackages não gerenciados (incluindo aqueles gerados pelo modelo de pacote do Visual Studio) usam arquivos. rgs estilo ATL para armazenar informações de registro. O formato de arquivo. rgs é específico da ATL e, em geral, não pode ser consumido como está por uma ferramenta de criação de instalação. As informações de registro para o instalador do VSPackage devem ser mantidas separadamente. Por exemplo, os desenvolvedores podem manter arquivos no formato. reg em sincronia com as alterações de arquivo. rgs. Os arquivos. reg podem ser mesclados com o RegEdit para trabalho de desenvolvimento ou consumidos por um instalador.  
  
## <a name="registering-managed-vspackages"></a>Registrando VSPackages gerenciados  
 A ferramenta RegPkg lê os atributos de registro de um VSPackage gerenciado e pode gravar as informações diretamente no registro ou gravar arquivos. reg-Format que podem ser consumidos por um instalador.  
  
> [!NOTE]
> A ferramenta RegPkg não é redistribuível e não pode ser usada para registrar um VSPackage no sistema de um usuário.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Por que VSPackages não deve se registrar automaticamente no momento da instalação  
 Os instaladores do VSPackage não devem confiar no auto-registro. À primeira vista, manter os valores de registro de um VSPackage apenas na VSPackage em si parece uma boa ideia. Considerando que os desenvolvedores precisam dos valores de registro disponíveis para seu trabalho e teste de rotina, faz sentido evitar a manutenção de uma cópia separada dos dados do registro no instalador. O instalador pode contar com o próprio VSPackage para gravar valores de registro.  
  
 Embora seja bom, o Autoregistro tem várias falhas que o tornam inadequado para a instalação do VSPackage:  
  
- Com suporte correto para instalação, desinstalação, reversão de instalação e reversão de desinstalação exige que você crie quatro ações personalizadas para cada VSPackage gerenciada que se registra automaticamente chamando RegPkg.  
  
- Sua abordagem para suporte lado a lado pode exigir que você crie quatro ações personalizadas que invoquem RegSvr32 ou RegPkg para cada versão com suporte do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Uma instalação com módulos autoregistrados não pode ser revertida com segurança porque não há nenhuma maneira de informar se as chaves autoregistradas são usadas por outro recurso ou aplicativo.  
  
- DLLs autoregistradas às vezes se vinculam a DLLs auxiliares que não estão presentes ou estão na versão errada. Por outro lado, Windows Installer pode registrar DLLs usando as tabelas do registro sem dependência no estado atual do sistema.  
  
- O código de Autoregistro pode ter o acesso negado aos recursos de rede, como bibliotecas de tipos, se um componente for especificado como execução da fonte e estiver listado na tabela SelfReg. Isso pode fazer com que a instalação do componente falhe durante uma instalação administrativa.  
  
## <a name="see-also"></a>Consulte Também  
 [Windows Installer](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Registro de pacote gerenciado](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
