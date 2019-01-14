---
title: 'DA0002: VSPerfCorProf.dll está ausente | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0002
- vs.performance.2
- vs.performance.rules.DAVsPerfCorProfMissing
- vs.performance.rules.DA0002
ms.assetid: 76e614b3-ad7e-4b92-b7be-88dc1329be1d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9bb499a1c41bfd6744f18b1bf67424b6e3c4835e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967674"
---
# <a name="da0002-vsperfcorprofdll-is-missing"></a>DA0002: VSPerfCorProf.dll está ausente

|||  
|-|-|  
|ID de regra|DA0002|  
|Categoria|Uso das ferramentas de criação de perfil|  
|Métodos de criação de perfil|Criação de perfil usando as ferramentas de linha de comando VSPerfCmd e VSPerfASPNETCmd|  
|Mensagem|Parece que o arquivo foi coletado sem definir corretamente as variáveis de ambiente com *VSPerfCLREnv.cmd*. Símbolos de binários gerenciados podem não ser resolvidos.|  
|Tipo de regra|Informações|  

## <a name="cause"></a>Causa  
 O criador de perfil não conseguiu localizar *VSPerfCorProf.dll* durante a execução da criação de perfil. Este aviso ocorre quando as ferramentas de linha de comando para a coleta de dados do criador de perfil são usadas sem usar a ferramenta *VSPerfCLREnv.cmd* para inicializar as variáveis de ambiente necessárias. O aviso também pode acionar se outro criador de perfil está sendo executado quando iniciar as ferramentas de criação de perfil.  

## <a name="rule-description"></a>Descrição da regra  
 Variáveis de ambiente específicas devem ser definidas antes de executar a criação de perfil para o criador de perfil resolver os símbolos nos binários do .NET Framework. Este aviso sugere que a ferramenta *VSPerfCLREnv.cmd* não estava em execução antes da coleta dos dados de criação de perfil. Símbolos de binários gerenciados podem não ser resolvidos. Para obter mais informações sobre como usar as ferramentas de criação de perfil da linha de comando, confira [Profiling from the command-line](../profiling/using-the-profiling-tools-from-the-command-line.md) (Criando perfil da linha de comando)  

## <a name="how-to-fix-violations"></a>Como corrigir violações  
 Quando você estiver criando perfis para aplicativos gerenciados usando as ferramentas de linha de comando nas ferramentas de criação de perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], execute a ferramenta da linha de comando [VSPerfCLREnv](../profiling/vsperfclrenv.md) ferramenta de linha de comando antes de iniciar a coleta de dados.