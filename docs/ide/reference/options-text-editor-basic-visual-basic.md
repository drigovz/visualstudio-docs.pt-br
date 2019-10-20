---
title: Opções, Editor de Texto, Basic (VB), Avançado
ms.date: 01/16/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Visual_Basic.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.Editor
- VS.ToolsOptionsPages.Visual_Basic_Editor.Editor
- VS.ToolsOptionsPages.Text_Editor.Basic.SimplifiedEditorPage
- VS.ToolsOptionsPages.Text_Editor.Basic
- VS.ToolsOptionsPages.Text_Editor.Basic.Advanced
- VS.ToolsOptionsPages.Text_Editor.Basic.VB_Specific
helpviewer_keywords:
- Basic Text Editor Options dialog box
ms.assetid: 5a8cafca-f7b4-4a2d-92ce-6894a7673d00
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a07645597846bd85f3152da866a253b079bc3963
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666338"
---
# <a name="options-text-editor-basic-visual-basic-advanced"></a>Opções, Editor de Texto, Basic (Visual Basic), Avançado
A página de propriedades **Específico do VB**, na pasta **Básico** da pasta **Editor de Texto** da caixa de diálogo **Opções** (menu **Ferramentas**) inclui as seguintes propriedades:

## <a name="analysis"></a>Análise

- Habilitar análise de solução completa

   Permite a análise de código em todos os arquivos na solução, não apenas nos arquivos de código abertos. Para obter mais informações, confira [Análise de solução completa](../../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="using-directives"></a>Usando diretivas

- Colocar as diretivas “System” primeiro ao classificar os usos

   Quando selecionado, o comando **Remover e classificar usos** no menu de clique com o botão direito do mouse classifica as diretivas `using` e coloca os namespaces "System" no topo da lista.

- Separar usando grupos de diretivas

   Quando selecionado, o comando **Remover e classificar usos** no menu de clique com o botão direito do mouse separa as diretivas `using` inserindo uma linha vazia entre os grupos de diretivas que têm o mesmo namespace de raiz.

- Sugerir usos para tipos em assemblies de referência
- Sugerir usos para tipos em pacotes NuGet

   Quando essas opções estiverem selecionadas, uma [Ação Rápida](../quick-actions.md) estará disponível para instalar um pacote NuGet e para adicionar uma diretiva `using` para tipos não referenciados.

   ![Ação rápida para instalar o pacote NuGet no Visual Studio](media/nuget-lightbulb.png)

## <a name="highlighting"></a>Realce

 **Habilitar realce de referências e palavras-chave**

O editor de texto pode realçar todas as instâncias de um símbolo ou todas as palavras-chave em uma cláusula como `If..Then`, `While...End While` ou `Try...Catch...Finally`. Você pode navegar entre referências ou palavras-chave realçadas pressionando **Ctrl** + **Shift** + **Seta para baixo** ou **Ctrl**  + **Shift** + **Seta para cima**.

## <a name="outlining"></a>Estrutura de tópicos

**Habilitar modo de estrutura de tópicos**

Ao abrir um arquivo no editor de código, você pode exibir o documento no modo de estrutura de tópicos. Consulte [Estrutura de Tópicos](../../ide/outlining.md) para obter mais informações. Quando essa opção é selecionada, o recurso de estrutura de tópicos é ativado quando você abre um arquivo.

**Mostrar separadores de linha do procedimento**

O editor de texto indica o escopo visual dos procedimentos. Uma linha é desenhada nos arquivos de origem *.vb* do seu projeto nos locais listados na tabela a seguir:

|Local no arquivo de origem .vb|Exemplo de local da linha|
|---------------------------------|------------------------------|
|Após o encerramento de um constructo de declaração de bloco|–   No final de uma classe, estrutura, módulo, interface ou enumeração<br />–   Depois de uma propriedade, função ou sub<br />–   Não entre cláusulas get e set em uma propriedade|
|Depois de um conjunto de constructos de linha única|–   Depois das instruções de importação, antes de uma definição de tipo em um arquivo de classe<br />–   Depois de variáveis declaradas em uma classe, antes de qualquer procedimento|
|Depois de declarações de linha única (declarações de nível não de bloco)|–   Após instruções de importação, instruções de herdar, declarações de variável, declarações de evento, declarações de delegado e instruções de declaração DLL|

## <a name="block-structure-guides"></a>Guias de estrutura de bloco

Quando essa opção estiver selecionada, as linhas verticais serão exibidas no editor, alinhadas aos blocos de código estruturado, o que permite que você identifique facilmente os blocos individuais de código. Por exemplo, você verá uma linha entre `Sub` e `EndSub` em uma instrução `Sub`.

## <a name="editor-help"></a>Ajuda do Editor

**Reformatação automática do código** O editor de texto reformata seu código conforme o necessário. Quando essa opção é selecionada, o editor de códigos:

- Alinhará seu código com a posição correta de guia

- Redefinirá as maiúsculas e minúsculas de palavras-chave, variáveis e objetos para o formato correto

- Adicionará um `Then` ausente a uma instrução `If...Then`

- Adicionará parênteses a chamadas de função

- Adicionará aspas finais faltando a cadeias de caracteres

- Reformatará notação exponencial

- Reformatará datas

**Inserção automática de constructos finais**

Quando você digita, por exemplo, a primeira linha de uma declaração de procedimento `Sub Main`, e pressiona **Enter**, o editor de texto adiciona uma linha `End Sub` correspondente. Da mesma forma, se você adicionar um loop [For](/dotnet/visual-basic/language-reference/statements/for-next-statement), o editor de texto adicionará uma instrução `Next` correspondente. Quando essa opção é selecionada, o editor de código adiciona automaticamente o constructo final.

**Inserção automática de membros Interface e MustOverride**

Quando você confirma uma instrução `Implements` ou uma instrução `Inherits` para uma classe, o editor de texto insere protótipos para os membros que devem ser implementados ou substituídos, respectivamente.

**Habilitar sugestões para correção de erros**

O editor de texto pode sugerir soluções para erros comuns e permitir selecionar a correção apropriada, que então é aplicada ao seu código.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)
- [Opções, Editor de Texto, Todas as Linguagens, Guias](../../ide/reference/options-text-editor-all-languages-tabs.md)
