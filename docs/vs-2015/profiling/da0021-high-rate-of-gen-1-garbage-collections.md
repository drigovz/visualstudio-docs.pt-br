---
title: 'DA0021: alta taxa de coletas de lixo da Ger 1 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d901d09350af063a11e3d156f36a100df85e7718
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586926"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Alta taxa de coletas de lixo de Geração 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID da regra | DA0021 |  
| Categoria |. Uso do .NET Framework |  
| Métodos de criação de perfil | Todos |  
| Mensagem | Há uma taxa bem alta de coletas de lixo de Gen 1 que ocorrem. Se, por design, a maioria das estruturas de dados do programa for alocada e persistida por um longo tempo, normalmente, isso não será um problema. No entanto, se esse comportamento não for intencional, o aplicativo poderá estar fixando objetos. Caso não tenha certeza, você poderá coletar dados de alocação de memória do .NET e informações de tempo de vida do objeto para entender o padrão de alocação de memória usado pelo aplicativo.|  
| Tipo de regra | Informações |  
  
 Ao criar o perfil usando a amostragem, a memória do .NET ou métodos de contenção de recursos, é necessário coletar pelo menos 10 amostras para disparar essa regra.  
  
## <a name="cause"></a>Causa  
 Dados de desempenho do sistema que foram coletados durante a criação de perfil indicam que uma proporção significativa da memória dos objetos do.NET Framework foi recuperada na geração 1 de coleta de lixo em comparação com a coleta de lixo da geração 0.  
  
## <a name="rule-description"></a>Descrição da Regra  
 O CLR (Common Language Runtime) do Microsoft .NET fornece um mecanismo de gerenciamento automático de memória que usa um coletor de lixo para recuperar a memória de objetos que não são mais usados pelo aplicativo. O coletor de lixo é orientado a geração, com base na suposição de que muitas alocações são de curta duração. Variáveis locais, por exemplo, devem ser de curta duração. Os objetos recém-criados iniciam na geração 0 (ger 0), em seguida, progridem para a geração 1 quando sobrevivem a uma execução da coleta de lixo e, por fim, fazem a transição para a geração 2 se ainda são usados pelo aplicativo.  
  
 Objetos na geração 0 são coletados com frequência e, em geral, de forma muito eficiente. Objetos na geração 1 são coletados com menos frequência e de forma menos eficiente. Por fim, objetos de longa duração na geração 2 devem ser coletados com uma frequência ainda menor. A coleta da geração 2, que é uma execução de coleta de lixo completa, também é a operação mais cara.  
  
 Essa regra é acionada quando ocorreu, proporcionalmente, um excesso de coletas de lixo da geração 1. Se um excesso de objetos de duração relativamente curta sobreviverem à coleta da geração 0, mas em seguida conseguirem serem coletados em uma coleta da geração 1, o custo de gerenciamento de memória poderá se tornar excessivo. Para obter mais informações, consulte a postagem [Mid-life crisis](https://docs.microsoft.com/archive/blogs/ricom/mid-life-crisis) (Crise de meia vida útil) em Performance Tidbits (Notícias sobre desempenho) de Rico Mariani no site do MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Como investigar um aviso  
 Clique duas vezes na mensagem da janela Lista de Erros para navegar para a [Exibição de Marcas](../profiling/marks-view.md) dos dados de criação de perfil. Encontre as colunas **Memória do .NET CLR\\Nº de coletas da Ger 0** e **Memória do .NET CLR\\Nº de coletas da Ger 1**. Determine se há fases específicas da execução do programa em que a coleta de lixo ocorre com mais frequência. Compare esses valores com a coluna **% de tempo no GC** para ver se o padrão de alocações de memória gerenciada está causando um excesso de sobrecarga de gerenciamento de memória.  
  
 Para entender o padrão do aplicativo de uso de memória gerenciada, crie o perfil dele novamente executando um perfil de alocação de Memória do.NET e solicite medições do Tempo de Vida do Objeto.  
  
 Para obter informações sobre como melhorar o desempenho da coleta de lixo, consulte [Garbage Collector Basics and Performance Hints](https://msdn2.microsoft.com/library/ms973837.aspx) (Noções básicas sobre o coletor de lixo e dicas de desempenho) no site da Microsoft. Para obter informações sobre a sobrecarga de coleta de lixo automática, consulte [O que há por trás do heap de objetos grandes](https://msdn.microsoft.com/magazine/cc534993.aspx).
