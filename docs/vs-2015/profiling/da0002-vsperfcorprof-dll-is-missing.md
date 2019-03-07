---
title: 'DA0002: VSPerfCorProf.dll está ausente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5723506415a0ddbf816b896e23e93eaa706bf7e7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54792917"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll não foi encontrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id da regra | DA0002 |  
| Categoria | Uso das ferramentas de criação de perfil |  
| Métodos de criação de perfil | Criação de perfil usando as ferramentas de linha de comando VSPerfCmd e VSPerfASPNETCmd |  
| Mensagem | Parece que o arquivo foi coletado sem definir corretamente as variáveis de ambiente com vsperfclrenv. cmd. Os símbolos de binários gerenciados podem não ser resolvidos.|  
| Tipo de regra | Informações |  
  
## <a name="cause"></a>Causa  
 O criador de perfil não conseguiu localizar VSPerfCorProf.dll durante o processo de criação de perfil. Este aviso ocorre quando as ferramentas de linha de comando para a coleta de dados do criador de perfil são usadas sem usar a ferramenta VSPerfCLREnv.cmd para inicializar as variáveis de ambiente necessárias. O aviso também pode acionar se outro criador de perfil está sendo executado quando iniciar as ferramentas de criação de perfil.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Variáveis de ambiente específicas devem ser definidas antes de executar a criação de perfil para o criador de perfil resolver os símbolos nos binários do .NET Framework. Esse aviso sugere que a ferramenta VSPerfCLREnv.cmd não foi executada antes dos dados de criação de perfil serem coletados. Símbolos de binários gerenciados podem não ser resolvidos. Para obter mais informações sobre como usar as ferramentas de criação de perfil da linha de comando, confira [Criação de perfil a partir da linha de comando](../profiling/using-the-profiling-tools-from-the-command-line.md)  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Quando você estiver criando perfis para aplicativos gerenciados usando as ferramentas de linha de comando nas ferramentas de criação de perfil do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], execute a ferramenta da linha de comando [VSPerfCLREnv](../profiling/vsperfclrenv.md) ferramenta de linha de comando antes de iniciar a coleta de dados.
