---
title: Como estender o código gerado pelo o-R Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665954"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Como: Estender o código gerado por object relational Designer de Objetos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O código gerado por [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] é regenerado quando alterações são feitas a classes de entidade e outros objetos ocorrem no designer. Devido a essa regeneração de código, qualquer código que você adicionar ao código gerado seja substituído normalmente quando o código de regenerados de designer. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] fornece a capacidade de gerar os arquivos parciais da classe em que você pode adicionar código que não será substituído. Um exemplo de adicionar seu próprio código para o código gerado por [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] está adicionando validação de dados para as classes LINQ to SQL (entidade). Para obter informações, consulte [como: Adicionar validação a classes de entidade](../data-tools/how-to-add-validation-to-entity-classes.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>Adicionando código para uma classe de entidade

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Para criar uma classe parcial e adicione o código para uma classe de entidade

1. Abra ou crie um novo arquivo de classes de LINQ to SQL (arquivo **. dbml** ) no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Clique duas vezes no arquivo **. dbml** em **Gerenciador de soluções** / **Gerenciador de banco de dados**.)

2. No [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , clique com o botão direito do mouse na classe para a qual você deseja adicionar a validação e clique em **Exibir código**.

     O editor de códigos abre com uma classe parcial para a classe de entidade selecionada.

3. Adicione o código na declaração de classe parcial para a classe de entidade.

## <a name="adding-code-to-a-datacontext"></a>Adicionando código para um DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Para criar uma classe parcial e adicione o código a um DataContext

1. Abra ou crie um novo arquivo de classes de LINQ to SQL (arquivo **. dbml** ) no [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Clique duas vezes no arquivo **. dbml** em **Gerenciador de soluções** / **Gerenciador de banco de dados**.)

2. No [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , clique com o botão direito do mouse em uma área vazia no designer e clique em **Exibir código**.

     O editor de códigos abre com uma classe parcial para o DataContext.

3. Adicione o código na declaração de classe parcial para o DataContext.

## <a name="see-also"></a>Consulte Também
 [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [passo a passos: criando classes de LINQ to SQL (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [passo a passos: adicionando validação a classes de entidade](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
