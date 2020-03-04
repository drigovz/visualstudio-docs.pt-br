---
title: 'Passo a passo: Configurando e usando um conjunto de regras personalizado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645747"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Passo a passo: Configurando e usando um conjunto de regras personalizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial mostra como usar ferramentas de análise de código que foram configuradas para usar um *conjunto de regras* personalizadas em uma biblioteca de classes. Você pode selecionar um conjunto de regras relacionado ao tipo de projeto que você especificou para sua solução, ou pode selecionar conjuntos de regras alternativos para atender a uma necessidade específica, como a verificação de código herdado para problemas que podem ser corrigidos de forma não-quebrada. Em ambos os casos, os conjuntos de regras também podem ser personalizados para ajustá-los aos requisitos do projeto.

 Neste tutorial, você irá percorrer esses processos:

- Crie uma biblioteca de classes.

- Selecione o conjunto de **regras de diretrizes de design básico da Microsoft** regra de análise de código.

- Adicione seu próprio código à classe.

- Executar análise de código.

- Personalize o conjunto de regras.

- Execute a análise de código e veja como funciona o comportamento de personalização do conjunto de regras.

## <a name="prerequisites"></a>Prerequisites

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] ou [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Usando conjuntos de regras com análise de código
 Primeiro, crie uma biblioteca de classes simples.

#### <a name="create-a-class-library"></a>Criar uma biblioteca de classes

1. No menu **arquivo** , clique em **novo** e em **projeto**.

2. Na caixa de diálogo **novo projeto** , em **tipos de projeto**, clique em **C#Visual**.

3. Em **Visual C#** , selecione **biblioteca de classes**.

4. Na caixa de texto **nome** , digite **RuleSetSample** e clique em **OK**.

   Em seguida, você selecionará o conjunto de regras de **diretrizes de design básico da Microsoft** e o salvará com seu projeto.

#### <a name="select-a-code-analysis-rule-set"></a>Selecionar um conjunto de regras de análise de código

1. No menu **analisar** , clique em **Configurar análise de código para RuleSetSample**.

    As definições de configuração para análise de código são exibidas.

2. Na lista suspensa **executar esta regra definida** , selecione **todas as regras da Microsoft**.

    Para obter mais informações sobre os conjuntos de regras disponíveis, consulte [referência de conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md).

    No menu arquivo, clique em **salvar itens selecionados** para atualizar o arquivo de projeto com informações sobre o conjunto de regras que você selecionou e suas configurações.

   > [!TIP]
   > Em uma situação real, uma prática recomendada é usar para priorizar quais problemas você deseja direcionar com a análise de código é começar com o conjunto de regras **mínimo recomendado** e corrigir os problemas desejados e, em seguida, adicionar de forma incremental mais regras ou conjuntos de regra a Encontre e corrija os problemas adicionais.

   Em seguida, você adicionará um código à biblioteca de classes que será usado para demonstrar violações da regra de análise de código do CA1704 "identificadores devem ser escritos corretamente". Para obter mais informações, consulte [CA1704: Os identificadores devem ser escritos corretamente ](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Adicione seu próprio código

- No Gerenciador de Soluções, abra o arquivo Class1.cs e substitua o código existente pelo seguinte:

  ```
  using System;
  using System.Collections.Generic;
  using System.Text;

  namespace RuleSetSample
  {
      public class Class1
      {
          //The variable parameter names "a" and "b" will cause
          //the warning CA 1704 Microsoft.Naming "Consider
          //providing a more meaningful name" to fire
          public int AddIntegers(int a, int b)
          {

              int sum = a + b;

              return (sum);
          }
      }
  }

  ```

  Agora você pode executar a análise de código no projeto RuleSetSample e procurar erros e avisos gerados na janela Lista de Erros.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Executar análise de código no projeto RuleSetSample

1. No menu **analisar** , clique em **executar análise de código em RuleSetSample**.

2. Na janela Lista de Erros, clique em **avisos** e, em seguida, clique no cabeçalho da coluna **Descrição** para classificar os avisos de forma alfanumérica.

    Em um aplicativo do mundo real, você corrigiria quaisquer violações de regra que valem a pena ser corrigidas neste ponto ou, opcionalmente, desativar ou suprimir uma regra se você determinou que ela não vale a pena ser corrigida. Para obter mais informações, confira [Suprimir avisos usando o atributo SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Observe os avisos do CA1704. Essas violações nessa regra indicam que você deve "considerar fornecer um nome mais significativo para os parâmetros". Você pode corrigir o problema em seu código ou desabilitar a regra, conforme explicado no próximo procedimento.

   Em seguida, você personalizará o conjunto de regras para excluir o aviso CA1704, "os identificadores devem ser escritos corretamente".

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Personalizar o conjunto de regras para o seu projeto para desabilitar uma regra específica

1. No menu **analisar** , clique em **Configurar análise de código para RuleSetSample**.

2. Na lista suspensa **executar esta regra definida** , verifique se o conjunto de regras de **todas as regras do Microsoft** ainda está realçado e clique em **abrir**. A página conjunto de regras é exibida.

3. Expanda o nó de categoria Microsoft. Naming e, em seguida, selecione o aviso CA1704.

4. Na coluna **ação** , selecione **nenhum.** Isso impede que o CA1704 seja exibido como um aviso ou erro na janela de Lista de Erros.

    Agora seria um bom momento para experimentar os vários botões da barra de ferramentas e opções de filtragem para se familiarizar com eles. Por exemplo, você pode usar a lista suspensa **Agrupar por** para ajudar a localizar uma regra específica ou uma categoria de regras. Outro exemplo é que você pode usar o botão **ocultar regras desabilitadas** na barra de ferramentas de páginas de conjunto de regras para ocultar ou mostrar todas as regras com a coluna **ação** definida como **nenhuma**. Isso pode ser útil se você quiser verificar se há alguma regra desativada para verificar se ainda deseja desabilitá-las.

5. No menu Exibir, clique em Janela de Propriedades. Digite **meu conjunto de regras personalizadas** na caixa nome da janela de ferramentas Propriedades. Isso altera o nome de exibição do novo conjunto de regras no [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] IDE.

6. No menu **arquivo** , clique em **salvar Microsoft All Rules. RuleSet** para salvar seu conjunto de regras personalizado. Navegue até a pasta raiz do seu projeto. Na caixa **de texto nome de arquivo** , digite **MyCustomRuleSet**. O conjunto de regras personalizadas agora pode ser selecionado para uso com seu projeto.

   Com o novo conjunto de regras criado, agora você precisa definir as configurações do projeto para especificar que deseja usar o novo conjunto de regras com ele.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Especifique o novo conjunto de regras para uso com seu projeto

1. Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto e selecione **Propriedades**.

2. Na guia **Propriedades** , clique em **análise de código**.

    Na lista suspensa **executar este conjunto de regras** , clique em **\<Browse.. >** . Navegue até a pasta raiz do seu projeto de código e, em seguida, selecione **MyCustomRuleSet. RuleSet**. Esse é o novo conjunto de regras que você criou no procedimento anterior.

3. No menu **arquivo** , clique em **salvar** para salvar a configuração do projeto. O conjunto de regras personalizado agora pode ser usado com seu projeto.

   Por fim, você executará a análise de código novamente usando o conjunto de regras MyCustomRuleSet. Observe que a janela Lista de Erros não exibe a violação da regra de desempenho CA1704.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Executar a análise de código no projeto RuleSetSample pela segunda vez

1. No menu **analisar** , clique em **executar análise de código em RuleSetSample**.

2. Na janela Lista de Erros, observe que quando você clica em **avisos**, não vê mais as violações de aviso CA1704 para a regra "identificadores devem ser escritos corretamente".

## <a name="see-also"></a>Consulte também
 [Como: Configurar a análise de código para um projeto de código gerenciado ](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [referência de conjunto de regras de análise de código](../code-quality/code-analysis-rule-set-reference.md)
