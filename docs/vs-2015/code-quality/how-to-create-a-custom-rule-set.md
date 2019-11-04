---
title: 'Como: Criar um conjunto de regras personalizado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e4aef02a2bb320112d7d268da28cf66b1ec6751
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657444"
---
# <a name="how-to-create-a-custom-rule-set"></a>Como: Criar um conjunto de regras personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsPro](../includes/vspro-md.md)], você pode criar e modificar um conjunto de *regras* personalizadas para atender às necessidades específicas do projeto associadas à análise de código. Para criar um conjunto de regras personalizado, você abre um ou mais conjuntos de regras padrão no editor de conjunto de regras. Você pode adicionar ou remover regras específicas e pode alterar a ação que ocorre quando a análise de código determina que uma regra foi violada.

 Para criar um novo conjunto de regras personalizadas, salve-o usando um novo nome de arquivo. O conjunto de regras personalizadas é atribuído automaticamente ao projeto.

## <a name="opening-the-rule-set-editor"></a>Abrindo o editor de conjunto de regras

#### <a name="to-open-an-empty-rule-set-file-in-the-rule-set-editor"></a>Para abrir um arquivo de conjunto de regras vazio no editor de conjunto de regras

1. No menu **arquivo** do [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], aponte para **novo** e clique em **arquivo**.

2. Na caixa de diálogo **novo arquivo** , clique em **geral** na lista **modelos instalados** e selecione conjunto de **regras de análise de código**.

3. O editor de conjunto de regras é exibido. Nenhuma regra é selecionada na lista editor.

#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para criar uma regra personalizada com base em um único conjunto de regras existente

1. Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Propriedades**.

2. Na guia **Propriedades** , clique em **análise de código**.

3. Na lista suspensa **conjunto de regras** , siga um destes procedimentos:

   - Selecione o conjunto de regras que você deseja personalizar.

     \- ou -

   - Selecionar **\<Browse... >** especificar um conjunto de regras existente que não esteja na lista.

4. Clique em **abrir** para exibir as regras no editor de conjunto de regras.

#### <a name="to-create-a-custom-rule-set-from-multiple-existing-rule-sets"></a>Para criar um conjunto de regras personalizadas de vários conjuntos de regras existentes

1. Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Propriedades**.

2. Na guia **Propriedades** , clique em **análise de código**.

3. Selecione **\<Choose vários conjuntos de regras... >** **executar este conjunto de regras**.

4. Na caixa de diálogo **Adicionar ou remover conjuntos de regras** , selecione os conjuntos de regras nos quais você deseja basear o novo conjunto de regras e clique em **OK**.

5. Salve o novo conjunto de regras.

     O nome do novo conjunto de regras é selecionado na lista **executar este conjunto de regras** . Você pode alterar o nome de exibição do conjunto de regras na próxima etapa.

6. Adicional Para alterar o nome de exibição do conjunto de regras, no menu **Exibir** , clique em **janela de propriedades**. Digite o nome de exibição na caixa **nome** .

7. Para adicionar, remover ou modificar regras específicas de análise de código no novo conjunto de regras, clique em **abrir**.

## <a name="modifying-a-rule-set"></a>Modificando um conjunto de regras

#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar um conjunto de regras no editor de conjunto de regras

- Para alterar o nome de exibição do conjunto de regras, no menu **Exibir** , clique em **janela de propriedades**. Insira o nome de exibição na caixa **nome** . Observe que o nome de exibição pode ser diferente do nome do arquivo.

- Para adicionar todas as regras do grupo a um conjunto de regras personalizadas, marque a caixa de seleção do grupo. Para remover todas as regras do grupo, desmarque a caixa de seleção.

- Para adicionar uma regra específica ao conjunto de regras personalizadas, marque a caixa de seleção da regra. Para remover a regra do conjunto de regras, desmarque a caixa de seleção.

- Para alterar a ação realizada quando uma regra é violada em uma análise de código, clique no campo **ação** para a regra e, em seguida, selecione um dos seguintes valores:

     **Warn** – gera um aviso.

     **Erro** -gera um erro.

     **Nenhum** – desabilita a regra. Essa ação é a mesma que remover a regra do conjunto de regras.

## <a name="changing-the-rule-set-editor-display"></a>Alterando a exibição do editor de conjunto de regras

#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar ou alterar os campos no editor de conjunto de regras usando a barra de ferramentas do editor de conjunto de regras

- Para expandir as regras em todos os grupos, clique em **expandir tudo**.

- Para recolher as regras em todos os grupos, clique em **recolher tudo**.

- Para alterar o campo pelo qual as regras são agrupadas, selecione o campo na lista **Agrupar por** . Para exibir as regras desagrupadas, selecione **\<None >** .

- Para adicionar ou remover campos em colunas de regra, clique em **Opções de coluna**.

- Para ocultar regras que não se aplicam à solução atual, **oculte as regras que não se aplicam à solução atual**.

- Para alternar entre mostrar e ocultar regras que recebem a ação de erro, clique em **Mostrar regras que podem gerar erros de análise de código**.

- Para alternar entre mostrar e ocultar regras que recebem a ação de aviso, clique em **Mostrar regras que podem gerar avisos de análise de código**.

- Para alternar entre mostrar e ocultar regras que são atribuídas à ação **nenhum** , clique em **Mostrar regras que não estão habilitadas**.

- Para adicionar ou remover conjuntos de regras padrão da Microsoft para o conjunto de regras atual, clique em **Adicionar ou remover conjuntos de regras filho**.

## <a name="see-also"></a>Consulte também
 [Como: Configurar a análise de código para um projeto de código gerenciado ](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [referência de conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md)
