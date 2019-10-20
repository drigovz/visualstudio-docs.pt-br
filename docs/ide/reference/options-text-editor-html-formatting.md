---
title: Opções, Editor de Texto, HTML (Web Forms), Formatação
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d1e5f07a2b68d86051452a16ac0f42fc9b9acf0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666202"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>Opções, Editor de Texto, HTML (Web Forms), Formatação

Use a página de opções de **Formatação** para definir opções do projeto em HTML para formatação de códigos no Editor de Códigos. Para acessar essa página, na barra de menus, escolha **Ferramentas** > **Opções** e expanda **Editor de Texto** > **HTML (Web Forms** > **Formatação**.

## <a name="capitalization"></a>Uso de maiúsculas

Quando essas opções são selecionadas, a exibição e editores XML de origem aplicam um formato padrão dos casos os nomes de elementos e atributos quando os elementos são criados durante o primeiro e formatação automática. As configurações de **Aplicar Formatação Automática** determinam o horário da reformatação automática.

> [!WARNING]
> XML diferencia maiúsculas de minúsculas. Definir casos padrão pode afetar analisadores XML.

### <a name="uielement-list"></a>Lista UIElement

**Marca de servidor, Atributos do servidor**

Essas opções especificam como a marcação para controles de servidor Web é capitalizada.

|Opção|Resultado|
|---------------------------------|------------------------------|
|**Como inserido**|A capitalização do elemento fica exatamente como foi inserida.|
|**Maiúsculas**|Nomes de elementos são reformatados para maiúsculas.|
|**Minúsculas**|Nomes de elementos são reformatados para minúsculas.|
|**Definição do assembly**|A capitalização do elemento é determinada pelo modo como o elemento é definido na classe de tipo correspondente.|

**Marca de cliente, Atributos do cliente**

Essas opções especificam se a formatação automática altera os nomes dos atributos e das propriedades HTML para maiúsculas ou minúsculas, ou se os mantêm como foram inseridos.

|Opção|Resultado|
|---------------------------------|------------------------------|
|**Como inserido**|A capitalização do atributo fica exatamente como foi inserida.|
|**Maiúsculas**|Os nomes de atributo são reformatados para maiúsculas.|
|**Minúsculas**|Os nomes de atributo são reformatados para minúsculas.|

## <a name="automatic-formatting-options"></a>Opções de formatação automática

Essas opções fazem com que o Editor de exibição do código-fonte adicione ou remova quebras de linha física durante a formatação automática. Você também pode especificar se o editor adiciona aspas aos atributos.

> [!NOTE]
> Essas configurações não alteram o espaço em branco na marcação XML.

### <a name="uielement-list"></a>Lista UIElement

- **Inserir aspas ao valor do atributo ao digitar**

   Quando essa opção é selecionada, o editor coloca automaticamente os atributos entre aspas à medida que você está digitando (por exemplo: ID = "Select1"). Desmarque esta opção se você preferir manualmente inserir aspas na marcação.

   > [!NOTE]
   > Se esta opção está selecionada, qualquer aspas existente - as marcas na marcação são retidas; aspas são removidas nunca.

- **Inserir aspas ao valor do atributo ao formatar**

   Quando essa opção é selecionada, a formatação automática adiciona aspas ao contrário dos valores de atributo (por exemplo: ID = "Select1").

   > [!NOTE]
   > Se esta opção está selecionada, qualquer aspas existente - as marcas na marcação são retidas.

- **Inserir automaticamente a marca de fechamento**

   Quando esta opção é selecionada, o editor cria automaticamente uma marca de fechamento (por exemplo, **\</b>** ) quando você fecha a marca de abertura.

## <a name="tag-wrapping"></a>Quebra automática de marca

Essas opções determinam se o editor quebrará marcas em linhas se elas excederem um certo tamanho.

### <a name="uielement-list"></a>Lista UIElement

- **Quebrar marcas ao exceder o comprimento especificado**

   Quando esta opção está selecionada, o editor quebrará marcas nas linhas se a marca exceder o comprimento especificado na caixa de texto **Comprimento**. Essa ação ocorre apenas ao formatar a marca, não ao digitar uma nova marca.

   > [!NOTE]
   > O valor que você especifica é usado como um valor mínimo. O editor não divide atributos individuais.

- **Comprimento**

   Especifica o número de caracteres para exibir em uma linha antes que envolva. Essa caixa de entrada fica desabilitada a menos que a caixa **Quebrar marcas ao exceder o comprimento especificado** esteja marcada.

- **Opções Específicas à Marca**

   Exibe a caixa de diálogo **Opções Específicas à Marca**, que permite a definição de opções de formatação para marcas individuais ou grupos de marcas.

## <a name="see-also"></a>Consulte também

- [Caixa de diálogo Geral, Ambiente, Opções](../../ide/reference/general-environment-options-dialog-box.md)