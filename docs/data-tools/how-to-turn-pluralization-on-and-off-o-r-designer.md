---
title: 'Como: Ligar e desligar a pluralização (Designer Relacional de Objetos)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 34b25be50cee681ee9c45e446d86a6054099926b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103739"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Como: Ligar e desligar a pluralização (Designer Relacional de Objetos)
Por padrão, quando você arrasta objetos de banco de dados que têm nomes que terminam em s ou em ies de **Gerenciador de servidores** ou **Database Explorer** até o [LINQ to SQL das ferramentas no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), o os nomes das classes de entidade gerados são alterados de plural a singular. Isso é feito a representa mais precisamente o fato que a classe instanciado de entidade mapeia para um único registro de dados. Por exemplo, adicionando um `Customers` de tabela para o **Relational Designer** resulta em uma classe de entidade chamada `Customer` porque a classe conterá dados para apenas um único cliente.

> [!NOTE]
>  Pluralization está ativada por padrão somente na versão de língua inglesa do Visual Studio.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Para desativar o pluralization e sobre

1. No menu **Ferramentas**, clique em **Opções**.

2. Na caixa de diálogo **Opções**, expanda **Ferramentas de Banco de Dados**.

    > [!NOTE]
    >  Selecione **Mostrar todas as configurações** se o nó de **Ferramentas de Banco de Dados** não estiver visível.

3. Clique em **Designer Relacional de Objetos**.

4. Definir **Pluralização de nomes** para **Enabled** = **False** para definir o **Relational Designer** para que ele não altera os nomes de classe .

5. Definir **Pluralização de nomes** para **Enabled** = **True** para aplicar regras de pluralization os nomes de classe de objetos adicionados ao **relacional de objetos Designer**.

## <a name="see-also"></a>Consulte também

- [Ferramentas do LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)