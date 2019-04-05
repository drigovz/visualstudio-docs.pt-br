---
title: Criar consultas TableAdapter parametrizadas
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- TableAdapters, parameterized queries
- data [Visual Studio], searching data
- queries [Visual Studio], creating
- TableAdapters, searching data
- queries [Visual Studio], TableAdapters
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 49bc9f56a07319c9edad1522c5e44b0bb35e92a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927332"
---
# <a name="create-parameterized-tableadapter-queries"></a>Criar consultas TableAdapter parametrizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma consulta parametrizada retorna dados que atendem às condições de uma cláusula WHERE dentro da consulta. Por exemplo, você pode parametrizar uma lista de clientes para exibir apenas clientes em uma determinada cidade, adicionando `WHERE City = @City` ao final da instrução SQL que retorna uma lista de clientes.  
  
Você pode criar consultas TableAdapter parametrizadas no Designer de conjunto de dados. Você também pode criá-los em um aplicativo do Windows com o **parametrizar fonte de dados** comando as **dados** menu. O **parametrizar fonte de dados** comando cria os controles no formulário onde você pode inserir os valores de parâmetro e executar a consulta.  
  
> [!NOTE]
> Ao construir uma consulta parametrizada, use a notação de parâmetro que é específica para o banco de dados que você está codificando. Por exemplo, acesso e fontes dados OleDb usam o ponto de interrogação '?' para denotar parâmetros, portanto, a cláusula WHERE seria algo como: `WHERE City = ?`.  
  
> [!NOTE]
> As caixas de diálogo e comandos de menu que você vê podem diferir dos descritos na Ajuda, dependendo de suas configurações ativas ou a edição que você está usando. Para alterar suas configurações, vá para o **ferramentas** menu e selecione **Import and Export Settings**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="create-a-parameterized-tableadapter-query"></a>Criar uma consulta TableAdapter parametrizada 
  
- Crie um novo TableAdapter, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL. Para obter mais informações, consulte [criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
     - ou -  
  
- Acrescente uma consulta a um TableAdapter existente, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL.
  
### <a name="create-a-parameterized-query-while-designing-a-data-bound-form"></a>Criar uma consulta parametrizada durante a criação de um formulário de associação de dados  
  
1.  Selecione um controle no seu formulário que já esteja associado a um conjunto de dados. Para obter mais informações, consulte [controles de ligar o Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
2.  Sobre o **dados** menu, selecione**Add Query**.  
  
3.  Preencha a caixa de diálogo **Pesquisar Construtor de Critérios**, adicionando uma cláusula WHERE com os parâmetros desejados à instrução SQL.  
  
### <a name="add-a-query-to-an-existing-data-bound-form"></a>Adicionar uma consulta a um formulário de associação de dados existente  
  
1. Abra o formulário no **Designer de Formulários do Windows**.  
  
2. Sobre o **dados** menu, selecione **Add Query** ou **marcas inteligentes de dados**.  
  
   > [!NOTE]
   > Se **Adicionar Consulta** não estiver disponível no menu **Dados**, selecione um controle no formulário que exibe a fonte de dados no qual deseja adicionar a parametrização. Por exemplo, se o formulário exibir dados em um controle <xref:System.Windows.Forms.DataGridView>, selecione-o. Se o formulário exibir dados em controles individuais, selecione qualquer controle associado a dados.  
  
3. No **tabela de fonte de dados selecione** área, selecione o tablethat que você deseja adiciona a parametrização.  
  
4. Digite um nome na caixa **Nome da nova consulta** ao criar uma nova consulta.  
  
    - ou -  
  
    Selecione uma consulta na caixa **Nome da consulta existente**.  
  
5. No **texto de consulta** , digite uma consulta que usa parâmetros.  
  
6. Selecione **OK**.  
  
    Um controle para inserir o parâmetro e um botão **Carregar** são adicionados ao formulário em um controle <xref:System.Windows.Forms.ToolStrip>.  
  
   Parâmetros do TableAdapter podem ser atribuídos valores nulos quando você deseja consultar os registros que não têm nenhum valor atual. Por exemplo, considere a consulta a seguir que tem um `ShippedDate` parâmetro no seu `WHERE` cláusula:  
  
   ```sql
   SELECT CustomerID, OrderDate, ShippedDate  
   FROM Orders  
   WHERE (ShippedDate = @ShippedDate) OR  
   (ShippedDate IS NULL)  
   ```

Se esta fosse uma consulta em um TableAdapter, você pode consultar todos os pedidos que não foram enviados com o código a seguir:  
  
   [!code-csharp[VbRaddataTableAdapters#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form2.cs#8)]
   [!code-vb[VbRaddataTableAdapters#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form2.vb#8)]  
  
### <a name="enable-a-query-to-accept-null-values"></a>Habilitar uma consulta aceitar valores nulos  
  
1.  No **Dataset Designer**, selecione a consulta do TableAdapter que precisa aceitar valores de parâmetro nulo.  
  
2.  No **propriedades** janela, selecione **parâmetros**. Em seguida, pressione o botão de reticências (**...** ) para abrir o **Editor de coleção de parâmetros**.  
  
3.  Selecione o parâmetro que permite valores nulos e defina as **AllowDbNull** propriedade `true`.  
  
## <a name="see-also"></a>Consulte também

- [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)