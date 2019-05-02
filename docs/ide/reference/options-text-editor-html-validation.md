---
title: Opções, Editor de Texto, HTML (Web Forms), Validação
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d06674d476dd671f715d2f4c88bdd23852f78687
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778473"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Opções, Editor de Texto, HTML (Web Forms), Validação

Use a página de opções **Validação** para definir preferências de como o editor de HTML verifica a sintaxe de marcação HTML em seu documento. Para acessar essa página, na barra de menus, escolha **Ferramentas** > **Opções** e expanda **Editor de Texto** > **HTML (Web Forms** > **Validação**.

## <a name="validation"></a>Validação

- **Use o doctype para detecção do esquema de validação**

   Um esquema determina quais elementos, atributos e capitalização são válidos nesse esquema. Também determina as marcas e os atributos que estarão disponíveis no IntelliSense.

   Selecione esta opção se você deseja que o Visual Studio use o conteúdo da declaração de **<!DOCTYPE>** e o elemento **html** para determinar o esquema. Por exemplo, se você selecionar esta opção e a página contiver a declaração `<!DOCTYPE html>`, o Visual Studio usará o esquema HTML5. No entanto, se a marca **html** tiver um atributo **xmlns**, como `<html xmlns="http://www.w3.org/1999/xhtml">`, o Visual Studio usará o esquema XHTML5.

- **Destino quando nenhum doctype for encontrado**

   Escolha o esquema para validação quando não houver uma declaração **<!DOCTYPE>** na página.

  - **Mostrar erros**

     Marque a caixa de seleção para habilitar a validação. Se a caixa de seleção não estiver marcada, o editor não marcará erros de validação.

     As outras caixas de seleção permitem que você ajuste a validação especificando tipos de erro individuais que você deseja que o editor marque.

     > [!NOTE]
     > Alguns esquemas não oferecem opções marcar tipos individuais de erros. Por exemplo, se você escolher **XHTML 1.1** como o esquema de destino, todas as caixas de seleção de opção serão desabilitadas. Nesse caso, todos os tipos de erros serão marcados.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)