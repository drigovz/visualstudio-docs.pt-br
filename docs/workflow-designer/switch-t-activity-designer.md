---
title: Designer de atividade de Designer de Fluxo de Trabalho-switch &lt; T &gt;
description: Saiba como usar o designer de <T> atividade de switch para criar e configurar uma <T> atividade switch no designer de fluxo de trabalho.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 35dcc390dcf58e02a2c7c1fa2dba62840d433785
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882304"
---
# <a name="switcht-activity-designer"></a>Designer de atividade Switch\<T>

A atividade de <xref:System.Activities.Statements.Switch%601> avalia uma expressão especificada e executa a atividade de uma coleção de atividades cuja chave associado corresponde ao valor obtido de avaliação.

A **opção<designer \>** de atividade T é usada para criar e configurar uma <xref:System.Activities.Statements.Switch%601> atividade no designer de fluxo de trabalho.

## <a name="the-switchtactivity"></a>A \<T> atividade Switch

Uma atividade de <xref:System.Activities.Statements.Switch%601> contém <xref:System.Activities.Statements.Switch%601.Expression%2A> e um dicionário de <xref:System.Activities.Statements.Switch%601.Cases%2A>. Cada caso no dicionário consiste em um par que contém uma *chave* e uma atividade que serve como seu *valor* correspondente. A atividade de <xref:System.Activities.Statements.Switch%601> avalia <xref:System.Activities.Statements.Switch%601.Expression%2A> e o compara com cada uma das chaves. Se uma correspondência for encontrada, a atividade correspondente é executada. Somente uma correspondência é possível porque as chaves de dicionário devem ser exclusivos de acordo com o tipo de igualdade definido pelo comparer de igualdade de dicionário. Se nenhuma correspondência for encontrada, a atividade de <xref:System.Activities.Statements.Switch%601.Default%2A> é executada.

## <a name="how-to-use-the-switcht-activity-designer"></a>Como usar o designer de \<T> atividade de switch

Acesse o designer de atividade do **\<T> comutador** na categoria **fluxo de controle** da caixa de **ferramentas**. Depois de soltá-lo na Designer de Fluxo de Trabalho, ele exibe a caixa de diálogo **Selecionar tipos** para permitir que o usuário especifique o tipo genérico *T* usado na <xref:System.Activities.Statements.Switch%601> atividade. O valor padrão é **Int32**. Depois que o tipo genérico *T* tiver sido selecionado, uma **opção<\>** designer de t será adicionada ao designer de fluxo de trabalho.

A seguir estão as propriedades de **Switch<\> T** designer. Todas essas propriedades podem ser editadas na grade de propriedade. Alguns deless também podem ser editados na superfície de designer.

A tabela a seguir mostra as propriedades mais úteis de <xref:System.Activities.Statements.Switch%601> e descreve como elas são usadas no designer.

|Nome da propriedade|Obrigatório|Uso|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falso|Especifica o nome amigável do designer de atividade de <xref:System.Activities.Statements.Switch%601> . O valor padrão é switch<Int32 \> . O valor pode ser editado na janela **Propriedades** ou diretamente no cabeçalho do designer.<br /><br /> Embora não seja necessário <xref:System.Activities.Activity.DisplayName%2A> restrita, é uma prática recomendada usar um.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Especifica a expressão usada para comparar as chaves na coleção dos casos para determinar que casos a executar.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Especifica a atividade executada se nenhuma correspondência for encontrada. Clique no botão **Adicionar uma atividade** no designer para abrir a caixa **padrão** em que a atividade pode ser descartada.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Especifica os casos a ser avaliado. Para adicionar um caso, clique no botão **Adicionar novo caso** na parte inferior do **switch \<T>** designer. O botão será alterado para uma caixa de texto (a box de combinação se o tipo genérico selecionado ao adicionar a opção \<T> for String ou enum). Depois de adicionar uma chave na caixa **valor do caso** , a área do caso é expandida e uma atividade pode ser descartada onde o texto de dica "soltar atividade aqui" para definir a lógica de execução para o caso.|

Vários casos podem ser adicionados como as chaves dos casos não são duplicadas. Se não, uma caixa de diálogo de erro exibe relatar a chave especificada dos casos já existe e que você deve escolher uma chave diferente. No designer **de \<T> switch** , apenas uma área de caso pode estar na exibição expandida de cada vez. Se uma área dos casos está na visualização recolhida, clique na área dos casos para expandi-la. Observe que para casos, recolhidos de designer mostra o nome para exibição de atividade dentro dos casos no lado direito se houver. Caso contrário, ele mostra o botão **Adicionar uma atividade** que expande o caso se você clicar nele e permitirá que você adicione uma atividade.

Clique na chave de casos existentes altera a chave de um rótulo em uma caixa de texto para que você possa editar a chave dos casos.

Existem 2 maneiras de excluir casos:

- Selecione os casos e excluir-los.

- Selecione o caso, clique com o botão direito do mouse para exibir o menu de contexto e selecione **excluir**.

Observe que você deve selecionar os casos os próprios para excluir. Selecionando e excluindo a atividade dentro de um caso exclui somente a atividade não os casos.

## <a name="see-also"></a>Confira também

- [Fluxo de Controle](../workflow-designer/control-flow-activity-designers.md)
