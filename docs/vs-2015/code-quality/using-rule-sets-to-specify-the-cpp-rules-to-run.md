---
title: Usando conjuntos de regras para especificar C++ as regras a serem executadas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277857"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>Usando conjuntos de regras para especificar as regras do C++ para execução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] e [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)], você pode criar e modificar um *conjunto de regras* personalizadas para atender às necessidades específicas do projeto associadas à análise de código. Para criar um conjunto C++ de regras personalizado, um CC++ /projeto deve estar aberto no IDE do Visual Studio. Em seguida, abra um conjunto de regras padrão no editor de conjunto de regras e adicione ou remova regras específicas e, opcionalmente, altere a ação que ocorre quando a análise de código determina que uma regra foi violada.  
  
 Para criar um novo conjunto de regras personalizadas, salve-o usando um novo nome de arquivo. O conjunto de regras personalizadas é atribuído automaticamente ao projeto.  
  
## <a name="opening-the-rule-set-editor"></a>Abrindo o editor de conjunto de regras  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>Para criar uma regra personalizada com base em um único conjunto de regras existente  
  
1. No Gerenciador de Soluções, abra o menu de atalho do projeto e, em seguida, escolha **Propriedades**.  
  
2. Na guia **Propriedades** , escolha **análise de código**.  
  
3. Na lista suspensa **conjunto de regras** , siga um destes procedimentos:  
  
   - Escolha o conjunto de regras que você deseja personalizar.  
  
     \- ou –  
  
   - Escolha **\<procurar... >** especificar um conjunto de regras existente que não esteja na lista.  
  
4. Escolha **abrir** para exibir as regras no editor de conjunto de regras.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>Para modificar um conjunto de regras no editor de conjunto de regras  
  
- Para alterar o nome de exibição do conjunto de regras, no menu **Exibir** , escolha **janela de propriedades**. Insira o nome de exibição na caixa **nome** . Observe que o nome de exibição pode ser diferente do nome do arquivo.  
  
- Para adicionar todas as regras do grupo a um conjunto de regras personalizadas, marque a caixa de seleção do grupo. Para remover todas as regras do grupo, desmarque a caixa de seleção.  
  
- Para adicionar uma regra específica ao conjunto de regras personalizadas, marque a caixa de seleção da regra. Para remover a regra do conjunto de regras, desmarque a caixa de seleção.  
  
- Para alterar a ação realizada quando uma regra é violada em uma análise de código, escolha o campo de **ação** para a regra e, em seguida, escolha um dos seguintes valores:  
  
     **Warn** – gera um aviso.  
  
     **Erro** -gera um erro.  
  
     **Nenhum** – desabilita a regra. Essa ação é a mesma que remover a regra do conjunto de regras.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>Para agrupar, filtrar ou alterar os campos no editor de conjunto de regras usando a barra de ferramentas do editor de conjunto de regras  
  
- Para expandir as regras em todos os grupos, escolha **expandir tudo**.  
  
- Para recolher as regras em todos os grupos, escolha **recolher tudo**.  
  
- Para alterar o campo pelo qual as regras são agrupadas, escolha o campo na lista **Agrupar por** . Para exibir as regras desagrupadas, escolha **\<nenhum >** .  
  
- Para adicionar ou remover campos em colunas de regra, escolha **Opções de coluna**.  
  
- Para ocultar regras que não se aplicam à solução atual, escolha **ocultar regras que não se aplicam à solução atual**.  
  
- Para alternar entre mostrar e ocultar regras que são atribuídas à ação de erro, escolha **Mostrar regras que podem gerar erros de análise de código**.  
  
- Para alternar entre mostrar e ocultar regras que recebem a ação de aviso, escolha **Mostrar regras que podem gerar avisos de análise de código**.  
  
- Para alternar entre mostrar e ocultar regras que são atribuídas à ação **nenhum** , escolha **Mostrar regras que não estão habilitadas**.  
  
- Para adicionar ou remover conjuntos de regras padrão da Microsoft para o conjunto de regras atual, escolha **Adicionar ou remover conjuntos de regras filho**.
