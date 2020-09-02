---
title: Como ativar e desativar a pluralização (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665940"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Como habilitar e desabilitar a pluralização (Designer Relacional de Objetos)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por padrão, quando você arrasta objetos de banco de dados que têm nomes que terminam em s ou s de **Gerenciador de servidores** / **Gerenciador de banco de dados** nas [ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), os nomes das classes de entidade geradas são alterados de plural para singular. Isso é feito a representa mais precisamente o fato que a classe instanciado de entidade mapeia para um único registro de dados. Por exemplo, adicione uma tabela de clientes para os resultados de [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] em uma classe de entidade chamada Cliente porque a classe conterá dados para apenas um único cliente.

> [!NOTE]
> Pluralization está ativada por padrão somente na versão de língua inglesa do Visual Studio.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Para desativar o pluralization e sobre

1. No menu **Ferramentas** , clique em **Opções**.

2. Na caixa de diálogo **Opções**, expanda **Ferramentas de Banco de Dados**.

> [!NOTE]
> Selecione **Mostrar todas as configurações** se o nó de **Ferramentas de Banco de Dados** não estiver visível.

1. Clique em **Designer Relacional de Objetos**.

2. Defina **pluralização de nomes** como **habilitado**  =  **false** para definir o [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] para que ele não altere os nomes de classe.

3. Defina **pluralização de nomes** como **habilitado**  =  **true** para aplicar as regras de pluralização aos nomes de classe dos objetos adicionados ao [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

## <a name="see-also"></a>Consulte Também
 [LINQ to SQL ferramentas no visual studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [acessar dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
