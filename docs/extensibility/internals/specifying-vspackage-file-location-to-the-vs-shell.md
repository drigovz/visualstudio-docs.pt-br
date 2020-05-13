---
title: Especificando a localização do arquivo VSPackage para o VS Shell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f112da4e79bff06d12472f0af7a3fe47b2f25da4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704973"
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Especificando o local do arquivo do VSPackage para o Shell do VS
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve ser capaz de localizar o Conjunto DLL para carregar o VSPackage. Você pode localizá-lo de várias maneiras, como descrito na tabela a seguir.

| Método | Descrição |
| - | - |
| Use a chave de registro CodeBase. | A chave CodeBase pode [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ser usada para carregar o conjunto VSPackage a partir de qualquer caminho de arquivo totalmente qualificado. O valor da chave deve ser o caminho do arquivo para a DLL. Esta é a melhor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] maneira de carregar o conjunto do pacote. Essa técnica às vezes é referida como a "técnica de diretório de instalação privada/CodeBase". Durante o registro, o valor da base de código é <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> repassado para as classes de atributo de registro através de uma instância do tipo. |
| Coloque o DLL no diretório **PrivateAssemblies.** | Coloque a montagem no subdiretório **PrivateAssemblies** do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diretório. Os conjuntos localizados em **PrivateAssemblies** são detectados automaticamente, mas não são visíveis na caixa de diálogo **Adicionar referências.** A diferença entre **PrivateAssemblies** e **PublicAssemblies** é que as assembléias em **PublicAssemblies** são enumeradas na caixa de diálogo **Adicionar referências.** Se você optou por não usar a técnica "CodeBase/private installation directory", então você deve instalar no diretório **PrivateAssemblies.** |
| Use uma montagem com nome forte e a chave de registro da Assembléia. | A tecla Assembly pode ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usada para direcionar explicitamente para carregar um conjunto forte chamado VSPackage. O valor da chave deve ser o nome forte da montagem. |
| Coloque o DLL no diretório **PublicAssemblies.** | Finalmente, a montagem também pode ser colocada no subdiretório **PublicAssemblies.** Os conjuntos localizados em **PublicAssemblies** são detectados automaticamente e também serão [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]exibidos na caixa de diálogo **Adicionar referências** em .<br /><br /> Os conjuntos vspackage só devem ser colocados no diretório **PublicAssemblies** se contiverem componentes gerenciados que se destinam a ser reutilizados por outros desenvolvedores do VSPackage. A maioria das assembleias não atende a esse critério. |

> [!NOTE]
> Use assembléias assinadas com nome forte para todas as suas assembléias dependentes. Esses conjuntos também devem ser instalados em seu próprio diretório ou no cache de montagem global (GAC). Isso protege contra conflitos com assembléias que tenham o mesmo nome de arquivo base, conhecido como vinculação de nome fraco.
