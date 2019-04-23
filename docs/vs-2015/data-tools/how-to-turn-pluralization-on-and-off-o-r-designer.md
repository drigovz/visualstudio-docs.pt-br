---
title: 'Como: Ative em pluralization e off (Object Relational Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ab9315c428944de0b047192a789eac6aa654073
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098617"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Como: Ligar e desligar a pluralização (Designer Relacional de Objetos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por padrão, quando você arrasta objetos de banco de dados que têm nomes que terminam em s ou em ies de **Gerenciador de servidores**/**Database Explorer** até a [ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), os nomes das classes de entidade gerados são alterados de plural a única. Isso é feito a representa mais precisamente o fato que a classe instanciado de entidade mapeia para um único registro de dados. Por exemplo, adicione uma tabela de clientes para os resultados de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] em uma classe de entidade chamada Cliente porque a classe conterá dados para apenas um único cliente.  
  
> [!NOTE]
>  Pluralization está ativada por padrão somente na versão de língua inglesa do Visual Studio.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Para desativar o pluralization e sobre  
  
1. No menu **Ferramentas**, clique em **Opções**.  
  
2. Na caixa de diálogo **Opções**, expanda **Ferramentas de Banco de Dados**.  
  
> [!NOTE]
>  Selecione **Mostrar todas as configurações** se o nó de **Ferramentas de Banco de Dados** não estiver visível.  
  
1. Clique em **Designer Relacional de Objetos**.  
  
2. Definir **Pluralização de nomes** para **Enabled** = **False** para definir o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para que ele não altera os nomes de classe.  
  
3. Definir **Pluralização de nomes** para **Enabled** = **True** para aplicar regras de pluralization os nomes de classe de objetos adicionados ao [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
