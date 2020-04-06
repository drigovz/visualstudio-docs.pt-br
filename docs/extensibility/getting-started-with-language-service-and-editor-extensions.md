---
title: Começando com o Serviço de Idiomas e extensões de editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711306"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>Comece com o serviço de idiomas e extensões de editor
Você pode usar extensões de editor para adicionar recursos de serviço de idioma, como delineamento, correspondência de chaves, IntelliSense e lâmpadas à sua própria linguagem de programação ou a qualquer tipo de conteúdo. Você também pode personalizar a aparência e o comportamento do editor do Visual Studio, por exemplo, coloração de texto, margens, adornos e outros elementos visuais. Você também pode definir seu próprio tipo de conteúdo e especificar a aparência e o comportamento das visualizações de texto em que seu conteúdo é exibido.

 Para começar a escrever extensões de editor, use os modelos de projeto do editor que são instalados como parte do Visual Studio SDK. O Visual Studio SDK é um conjunto de ferramentas para download que facilitam o desenvolvimento de extensões do Visual Studio, seja usando VSPackages ou usando o Managed Extensibility Framework (MEF).

> [!NOTE]
> Para obter mais informações sobre o Visual Studio SDK, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 Recomendamos que você aprenda sobre os seguintes conceitos e tecnologias antes de escrever suas próprias extensões de editor.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>As extensões da Windows Presentation Foundation (WPF) e do editor
 A interface de usuário do editor do Visual Studio (UI) é implementada usando a Windows Presentation Foundation (WPF). O WPF proporciona uma rica experiência visual e um modelo de programação consistente que separa os aspectos visuais do código da lógica empresarial. Você pode usar muitos elementos e recursos do WPF quando criar extensões de editor. Para obter mais informações, consulte [Windows Presentation Foundation](/dotnet/framework/wpf/index).

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>O Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada) e as extensões do editor
 O editor do Visual Studio usa o Mef (Managed Extensibility Framework, estrutura de extensibilidade gerenciada) para gerenciar seus componentes e extensões. O MEF também permite que os desenvolvedores criem mais facilmente extensões para um aplicativo host como o Visual Studio. Neste quadro, você define uma extensão de acordo com um contrato MEF e exporta-a como uma parte componente MEF. O aplicativo host gerencia as partes componentes encontrando-as, registrando-as e certificando-se de que elas são aplicadas ao contexto correto.

> [!NOTE]
> Para obter mais informações sobre o MEF no editor, consulte [Managed Extensibility Framework no editor](../extensibility/managed-extensibility-framework-in-the-editor.md).

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Pontos e extensões do editor do Visual Studio
 Os pontos de extensão do editor são peças componentes MEF que você pode personalizar e estender. Em alguns casos, você estende o ponto de extensão implementando uma interface e exportando-a juntamente com os metadados corretos. Em outros casos, basta declarar uma extensão e exportá-la como um tipo específico.

 A seguir, alguns dos tipos básicos de extensões de editor:

- Margens e roltas

- Marcas

- Adornos

- Opções

- IntelliSense

  Para obter mais informações sobre pontos de extensão do editor, consulte [os pontos de extensão do serviço de idiomas e do editor](../extensibility/language-service-and-editor-extension-points.md).

## <a name="deploying-editor-extensions"></a>Implantação de extensões de editor
 No Visual Studio, você implanta extensões de editor adicionando um arquivo de metadados chamado *source.extension.vsixmanifest* à solução, construindo a solução e, em seguida, adicionando uma cópia dos arquivos binários e do manifesto em uma pasta que é conhecida pelo Visual Studio. O arquivo manifesto define os fatos básicos sobre a extensão (por exemplo, nome, autor, versão e tipo de conteúdo). Para obter mais informações sobre o arquivo manifesto VSIX e como implantar extensões, consulte [extensões do Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Quando você instalar uma extensão em um computador, inclua os binários e o manifesto em uma subpasta de pasta que é conhecida pelo Visual Studio.

> [!WARNING]
> Você não precisa se preocupar com os detalhes dos manifestos e locais de implantação se você usar um dos modelos de extensibilidade do editor que estão incluídos no Visual Studio. Os modelos contêm tudo o que é necessário para registrar e implantar uma extensão.

## <a name="run-extensions-in-the-experimental-instance"></a>Executar extensões na instância experimental
 Você pode isolar sua versão de trabalho do Visual Studio enquanto estiver desenvolvendo uma extensão implantando-a na seguinte pasta experimental (no Windows Vista e no Windows 7):

 *{%LOCALAPPDATA%}\VisualStudio\10.0Exp\Extensões\\{Empresa}\\{ExtensionID}*

 onde *%LOCALAPPDATA%* é o nome do usuário conectado, *Empresa* é o nome da empresa que possui a extensão, e *ExtensionID* é o ID da extensão.

 Quando você implanta uma extensão para o local experimental, ela é executada no modo de depuração. Uma segunda instância do Visual Studio é iniciada, e é chamada **Microsoft Visual Studio - Exemplo Experimental**.

## <a name="manage-extensions"></a>Gerenciar extensões
 As extensões do Visual Studio estão listadas em **Extensões e Atualizações** (no menu **Ferramentas).** Se você estiver testando uma extensão na instância experimental, ela será listada em **Extensões e Atualizações** na instância experimental, mas não está listada na instância de desenvolvimento.

 Para obter mais informações, consulte [Encontrar e usar extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

## <a name="use-templates-to-create-editor-extensions"></a>Use modelos para criar extensões de editor
 Você pode usar modelos de editor para criar extensões MEF que personalizem classificadores, adornos e margens. Existem modelos para projetos C# e Visual Basic. Para obter mais informações, consulte [Criar uma extensão com um modelo de item do editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

 Você também pode usar o modelo do Projeto VSIX para criar extensões. Este modelo fornece apenas os elementos necessários para implantar qualquer tipo de extensão e inclui o arquivo *source.extension.vsixmanifest,* as referências de montagem necessárias e um arquivo de projeto que inclui as tarefas de compilação que permitem implantar a extensão. Para obter mais informações, consulte [o modelo do projeto VSIX](../extensibility/vsix-project-template.md).

 Você também pode criar componentes mef do editor a partir de uma extensão do Visual Studio Package. Veja os seguintes passos para obter detalhes:

- [Passo a passo: Usando um comando shell com uma extensão de editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [Passo a passo: Usando uma chave de atalho com uma extensão de editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>Confira também
- [Pontos de extensão de serviços de idiomas e editores](../extensibility/language-service-and-editor-extension-points.md)
