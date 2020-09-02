---
title: Distribuindo aplicativos de shell isolados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204670"
---
# <a name="distributing-isolated-shell-applications"></a>Distribuir aplicativos de Shell isolado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você deve instalar o Visual Studio e o SDK do Visual Studio para criar um aplicativo de shell isolado. Para distribuir o aplicativo para os computadores de outros usuários ou clientes, você deve incluir um pacote redistribuível especial para o Shell isolado.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>Pré-requisitos para distribuir aplicativos de shell isolados  
  
|Name|Descrição|  
|----------|-----------------|  
|SDK do Visual Studio|O SDK é necessário para desenvolver e testar extensões do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Você também pode usar o SDK para criar sua própria instância do Shell isolado do Visual Studio.<br /><br /> O Visual Studio é um pré-requisito para o SDK.|  
|Microsoft Visual Studio redistribuível do Shell isolado|Os redistribuíveis incluídos no seu programa de instalação quando você cria um ambiente de ferramentas no Shell isolado do Visual Studio. O pacote redistribuível do Shell isolado inclui o .NET Framework 4,5.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>Criando um programa de instalação para o aplicativo  
 Você deve criar um programa de instalação especial para seu aplicativo de shell integrado ou isolado. Para obter mais informações, consulte [instalando um aplicativo de shell isolado](../extensibility/installing-an-isolated-shell-application.md).  
  
## <a name="allowing-for-updates-to-your-application"></a>Permitindo atualizações para seu aplicativo  
 Seu programa de instalação deve permitir a possibilidade de que seu aplicativo seja atualizado, seja pelo Microsoft Update ou pelas atualizações da sua empresa. Para obter mais informações sobre atualizações, consulte [diretrizes de manutenção para aplicativos de shell isolados](../extensibility/servicing-guidelines-for-isolated-shell-applications.md).
