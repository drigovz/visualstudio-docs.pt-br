---
title: Escolhendo entre VSPackages compartilhados e versados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739877"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Escolha entre VSPackages compartilhados e versões
Versões diferentes do Visual Studio podem coexistir no mesmo computador. VsPackages podem suportar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] qualquer mix de versões.

 Você pode habilitar instalações lado a lado de VSPackages através de uma das duas estratégias, a estratégia compartilhada ou a estratégia versionada. Ambos acomodam a presença [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de várias versões e versões associadas do .NET Framework.

 Na estratégia compartilhada, um VSPackage é registrado para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]uso em várias versões de . Na estratégia versionada, vários DLLs VSPackage são instalados, um para cada versão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do que você suporta.

## <a name="shared-vspackages"></a>VSPacotes compartilhados
 O uso de um VSPackage compartilhado é apropriado quando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]você usa o mesmo VSPackage em várias versões de . Para implementar um VSPackage compartilhado, você deve tomar as seguintes etapas:

- Torne seu VSPackage compatível [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]com várias versões de . Duas maneiras de fazê-lo estão disponíveis:

  - Limite seu VSPackage para usar apenas os [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] recursos da versão mais antiga do que você suporta.

  - Programe seu VSPackage para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se adaptar à versão em que está sendo executado. Então, se as consultas para serviços mais recentes falharem, seu VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]pode oferecer outros serviços que são suportados em versões mais antigas de .

- Registre seu VSPackage apropriadamente. Para obter mais informações, consulte [vsPackage registration](../extensibility/internals/vspackage-registration.md) and [Managed VSPackage registration](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Registre as extensões de arquivo apropriadamente. Para obter mais informações, consulte [Registrando extensões de nome de arquivo para implantações lado a lado](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Crie um instalador que implante seu VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]para as versões apropriadas de . Para obter mais informações, consulte [Instalando VSPackages com o gerenciamento do Instalador](../extensibility/internals/installing-vspackages-with-windows-installer.md) do Windows e [do Componente](../extensibility/internals/component-management.md).

- Abordar a questão das colisões de registro. Para obter mais informações, consulte [vsPackage registration](../extensibility/internals/vspackage-registration.md).

- Certifique-se de que os arquivos compartilhados e com versões respeitem a contagem de referências para permitir a instalação e a remoção seguras de várias versões. Para obter mais informações, consulte [Gerenciamento de componentes](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>VsPackages com versão
 Na estratégia VSPackage versão, você cria um VSPackage para cada versão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do que você suporta. Fazer isso é apropriado quando você espera aproveitar os [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]serviços fornecidos por versões posteriores de , porque cada VSPackage pode evoluir sem afetar os outros. No entanto, a estratégia versionada de criar vários binários, seja a partir de uma única base de código ou de várias bases de código independentes, pode implicar mais desenvolvimento inicial do que a estratégia compartilhada. Além disso, pode ser necessário um trabalho adicional de configuração porque você deve criar uma [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] configuração separada para cada versão ou uma única configuração que detecte as versões que estão instaladas e que o seu VSPackage suporta.

## <a name="binary-compatibility"></a>Compatibilidade binária
 Geralmente, a compatibilidade binária permite que vsPackages de código nativo desenvolvidos com versões anteriores do Visual Studio para serem executados em versões posteriores do Visual Studio. No entanto, há três exceções importantes:

- Se o vsPackage se baseia em uma versão específica do tempo de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] execução do idioma comum, então ele deve determinar em qual versão dele está sendo executada.

- Um VSPackage pode ter uma dependência de um recurso específico de outro VSPackage ou outro produto. Consequentemente, o VSPackage só pode ser executado onde a dependência está satisfeita.

- Um VSPackage pode ser afetado por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uma correção de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]segurança em um pacote de serviço ou uma versão posterior de . Nesses casos, um VSPackage desenvolvido com [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] uma versão anterior [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] do pode não ser executado em versões de depois que a correção de segurança foi aplicada. No entanto, você pode reconstruir seu pacote com a versão posterior e tê-lo também executado em versões anteriores.

  Os VSPackages gerenciados devem ser [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] construídos usando uma versão de e as [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] que correspondem à versão de destino de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

  Além de planejar a compatibilidade binária para seus binários VSPackage, você também deve considerar formatos de solução e arquivo de projeto. Se o VSPackage criar um novo tipo de projeto, você deve decidir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]se ele pode ser executado em apenas uma versão ou em várias versões de . Para obter mais informações, consulte [Atualizar projetos personalizados](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Confira também
- [Instalando pacotes VS com o instalador do Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Gerenciamento de componentes](../extensibility/internals/component-management.md)
