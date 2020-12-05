---
title: Ação rápida de geração de construtor
description: Saiba como usar o menu ações rápidas e refatoração para gerar imediatamente o código para um novo Construtor em uma classe.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 80de8b5c8b5699f4ddbf5148e16afd2da42388f2
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617546"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Gerar um construtor no Visual Studio

Esta geração de código aplica-se a:

- C#

- Visual Basic

**O quê:** permite gerar imediatamente o código para um novo construtor em uma classe.

**Quando:** você introduz um novo construtor e deseja declará-lo corretamente automaticamente, ou modifica um construtor existente.

**Por quê:** você poderia declarar o construtor antes de usá-lo; no entanto, esse recurso o gerará automaticamente com os parâmetros apropriados. Além disso, modificar um construtor existente exige a atualização de todos os callsites, a menos que você use este recurso para atualizá-los automaticamente.

**Como:** há várias maneiras de gerar um construtor:

- [Gerar construtor e selecionar membros](#pick)
- [Gerar Construtor com propriedades](#with)
- [Gerar Construtor a partir dos campos selecionados](#selection)
- [Gerar construtor desde uma nova utilização](#usage)
- [Adicionar o parâmetro ao construtor existente](#addparameter)
- [Criar e inicializar o campo/propriedade de um parâmetro de construtor](#create)

## <a name="generate-constructor-and-pick-members-c-only"></a><a id = "pick"></a> Gerar construtor e selecionar membros (somente C#)

1. Coloque o cursor em qualquer linha vazia em uma classe:

   ![Cursor em linha vazia](media/constructor1-highlight-cs.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Clique no :::image type="icon" source="media/screwdriver.png"::: ícone que aparece na margem esquerda se o cursor de texto já estiver na linha vazia da classe.

   ![Captura de tela da opção gerar Construtor.](media/constructor1-preview-cs.png)

1. Selecione **Gerar construtor** no menu suspenso.

   A caixa de diálogo **Selecionar membros** abre.

1. Selecione os membros que você deseja incluir como parâmetros do construtor. Você pode ordená-los usando as setas para cima e para baixo. Selecione **OK**.

   ![Caixa de diálogo Escolher membros](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Você pode marcar a caixa de diálogo **Adicionar verificações nulas** para gerar automaticamente verificações nulas para os parâmetros do construtor.

   O construtor é criado com os parâmetros especificados.

   ![Captura de tela mostrando que o construtor é criado com os parâmetros especificados.](media/constructor1-result-cs.png)

## <a name="generate-constructor-with-properties-c-only"></a><a id = "with"></a> Gerar Construtor com Propriedades (somente C#)

1. Coloque o cursor na instância.

2. Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.

3. Selecione **gerar Construtor em `<QualifiedName>` (com propriedades)**.

   ![Captura de tela do construtor de geração na opção de chave (com propriedades).](media/generate-constructor-with-properties.png)

## <a name="generate-constructor-from-selected-fields-c-only"></a><a id="selection"></a> Gerar construtor usando campos selecionados (somente C#)

1. Realce os membros que você deseja inserir no construtor gerado:

   ![Realçar membros](media/constructor2-highlight-cs.png)

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Clique no :::image type="icon" source="media/screwdriver.png"::: ícone que aparece na margem esquerda se o cursor de texto já estiver na linha com a seleção.

      ![Captura de tela da opção Generate Construtor Person String String.](media/constructor2-preview-cs.png)

1. Selecione **Gerar construtor 'TypeName(...)'** no menu suspenso.

   O construtor é criado com os parâmetros selecionados.

   ![Captura de tela mostrando que o construtor é criado com os parâmetros selecionados.](media/constructor2-result-cs.png)

## <a name="generate-constructor-from-new-usage-c-and-visual-basic"></a><a id="usage"></a> Gerar construtor de uso novo (C# e Visual Basic)

1. Coloque o cursor na linha em que há um rabisco vermelho. O rabisco vermelho indica uma chamada para um construtor que ainda não existe.

   - C#:

       ![Código em C# realçado](media/constructor-highlight-cs.png)

   - Visual Basic:

       ![Código em VB realçado](media/constructor-highlight-vb.png)

2. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Passe o mouse sobre o ondulado vermelho e clique no :::image type="icon" source="media/error-bulb.png"::: ícone que aparece.
      - Clique no :::image type="icon" source="media/error-bulb.png"::: ícone que aparece na margem esquerda se o cursor de texto já estiver na linha com o ondulado vermelho.

      ![Captura de tela da opção gerar Construtor na pessoa.](media/constructor-preview-cs.png)

3. Selecione **Gerar construtor em '*TypeName*'** no menu suspenso.

   > [!TIP]
   > Use o link **Visualizar alterações** na parte inferior da janela de visualização [para ver todas as alterações](../../ide/preview-changes.md) que serão feitas antes de fazer sua seleção.

   O construtor é criado, com os parâmetros inferidos com base em seu uso.

   - C#:

       ![Gerar o resultado do método C#](media/constructor-result-cs.png)

   - Visual Basic:

       ![Gerar o resultado do método VB](media/constructor-result-vb.png)

## <a name="add-parameter-to-existing-constructor-c-only"></a><a id="addparameter"></a> Adicionar parâmetro ao construtor existente (somente C#)

1. Adicione um parâmetro a uma chamada de construtor existente.

2. coloque o cursor na linha em que há um rabisco vermelho indicando que você usou um construtor que ainda não existe.

    ![Captura de tela mostrando a linha onde há um ondulado vermelho.](media/constructor4-highlight-cs.png)

3. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Passe o mouse sobre o ondulado vermelho e clique no :::image type="icon" source="media/error-bulb.png"::: ícone que aparece.
      - Clique no :::image type="icon" source="media/error-bulb.png"::: ícone que aparece na margem esquerda se o cursor de texto já estiver na linha com o ondulado vermelho.

      ![Captura de tela da opção de cadeia de caracteres Adicionar parâmetro à pessoa.](media/constructor4-preview-cs.png)

4. Selecione **Adicionar parâmetro em 'TypeName(...)'** no menu suspenso.

   O parâmetro é adicionado ao construtor, com o tipo inferido com base em seu uso.

   ![Captura de tela mostrando que o parâmetro é adicionado ao construtor, com seu tipo inferido de seu uso.](media/constructor4-result-cs.png)

Também é possível adicionar um parâmetro a um método existente. Para saber mais, confira [Adicionar parâmetro a um método](add-parameter.md).

## <a name="create-and-initialize-a-field-or-property-from-a-constructor-parameter-c-only"></a><a id="create"></a> Criar e inicializar um campo ou uma propriedade de um parâmetro de construtor (somente C#)

1. Localize um construtor existente e adicione um parâmetro:

   ![Captura de tela mostrando um Construtor existente.](media/constructor5-highlight-cs.png)

1. Coloque o cursor dentro do parâmetro recém-adicionado.

1. Depois, siga um destes procedimentos:

   - **Teclado**
      - Pressione **Ctrl** + **.** para acionar o menu **Ações e Refatorações Rápidas**.
   - **Mouse**
      - Clique com o botão direito do mouse e selecione o menu **Ações Rápidas e Refatorações**.
      - Clique no :::image type="icon" source="media/screwdriver.png"::: ícone que aparece na margem esquerda se o cursor de texto já estiver na linha com o parâmetro adicionado.

   ![Captura de tela da opção de idade de propriedade criar e inicializar.](media/constructor5-preview-cs.png)

1. Selecione **Criar e inicializar propriedade** ou **Criar e inicializar campo** no menu suspenso.

   O campo ou a propriedade é declarada e automaticamente nomeada para corresponder aos seus tipos. Uma linha de código também é adicionada para inicializar o campo ou a propriedade no corpo do construtor.

   ![Captura de tela mostrando que o campo ou propriedade é declarado e nomeado automaticamente para corresponder aos seus tipos.](media/constructor5-result-cs.png)

## <a name="see-also"></a>Confira também

- [Geração de código](../code-generation-in-visual-studio.md)
- [Visualizar alterações](../../ide/preview-changes.md)
