---
title: Modelo de projeto VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697931"
---
# <a name="vsix-project-template"></a>Modelo de projeto VSIX

Você pode usar o modelo do Projeto VSIX para envolver uma ou mais extensões do Visual Studio em um projeto VSIX e, em seguida, publicar o pacote no site do [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

 A implantação do VSIX suporta VSPacotes, conjuntos, componentes MEF, modelos de projeto, modelos de itens, controles de caixa de ferramentas e tipos de extensão personalizados.

> [!NOTE]
> Para usar projetos VSIX, você deve instalar o Visual Studio SDK. Para obter mais informações sobre o Visual Studio SDK, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Onde encontrar o modelo de projeto VSIX

O modelo do Projeto VSIX está disponível na caixa de diálogo **Do Novo Projeto,** procurando por "vsix".  Há uma versão C# e Visual Basic.

> [!TIP]
> Você deve certificar-se de que o .NET Framework 4.5 ou superior seja especificado na caixa de lista baixa na parte superior da caixa de diálogo **Novo Projeto.**

## <a name="uses-of-the-vsix-project-template"></a>Usos do modelo de projeto VSIX

O modelo de projeto VSIX tem dois usos principais:

- Para implantar modelos de projeto, modelos de itens e extensões.

- Para envolver as saídas de várias extensões em um pacote de implantação.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Empacotamento de uma extensão em um projeto VSIX vazio

Você pode empacotar uma extensão existente, ou uma extensão que ainda não tenha suporte vsix, embrulhando-a em um projeto VSIX vazio. A extensão a ser [embrulhada](../extensibility/vsix-extension-schema-2-0-reference.md)deve ser de um tipo que é suportado pelo esquema VSIX .

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Para empacotar uma extensão usando um projeto VSIX

1. Construa os projetos que compõem sua extensão.

2. Crie um projeto VSIX usando o modelo do **Projeto VSIX.**

    *Source.extension.vsixmanifest abre* em **Manifest Designer**.

3. Na guia **Ativos,** escolha o botão **Novo.**

    A caixa de diálogo **Adicionar novo ativo** é exibida.

4. Na lista **Tipo,** escolha o tipo de extensão a ser adicionado.

5. Para adicionar uma extensão ou elemento de conteúdo incluído na solução atual (por exemplo, um modelo de item ou um conjunto compilado), execute as seguintes etapas:

   1. Na lista **Origem,** escolha **Um projeto na solução atual**.

   2. Na lista **Projeto,** escolha o nome da extensão.

   3. Na caixa Incorporar nesta caixa **de pasta,** digite o nome de uma pasta na qual incorporar o ativo e, em seguida, escolha o botão **OK.**

6. Para adicionar uma extensão ou elemento de conteúdo que não esteja incluído na solução atual, execute as seguintes etapas:

   1. Na caixa **'Lista** de origem', escolha **Arquivo no sistema de arquivos**.

   2. No campo **Caminho,** digite o caminho completo para o arquivo de extensão compilado ou compactado ou use o botão **Procurar** para navegar até o arquivo.

   3. Na caixa Incorporar nesta caixa **de pasta,** digite o nome de uma pasta na qual incorporar o ativo e, em seguida, escolha o botão **OK.**

7. Se você quiser que seu pacote inclua extensões adicionais, adicione-as da mesma maneira.

8. Compile a solução.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]cria um arquivo *.vsix* que contém um arquivo manifesto VSIX, um arquivo *[Content_Types] .xml* e todos os ativos de extensão que você adicionou ao projeto.

## <a name="see-also"></a>Confira também

- [Referência do esquema de extensão VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Localizar e usar extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
