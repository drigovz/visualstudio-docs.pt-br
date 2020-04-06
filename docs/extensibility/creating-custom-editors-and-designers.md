---
title: Criando Editores e Designers Personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739480"
---
# <a name="create-custom-editors-and-designers"></a>Crie editores e designers personalizados

O Ambiente de Desenvolvimento Integrado (IDE) do Visual Studio pode hospedar diferentes tipos de editor:

- O editor principal do Visual Studio

- Editores personalizados

- Editores Externos

- Designers

As informações a seguir ajudam você a escolher o tipo de editor que você precisa.

## <a name="types-of-editor"></a>Tipos de editor

Para obter informações sobre o editor principal do Visual Studio, consulte [Estender o editor e os serviços de idiomas.](../extensibility/extending-the-editor-and-language-services.md)

### <a name="custom-editors"></a>Editores personalizados
 Um editor personalizado é aquele que foi projetado para trabalhar em circunstâncias especializadas. Por exemplo, você pode criar um editor cuja função é ler e gravar dados em um repositório específico, como um servidor Microsoft Exchange. Escolha um editor personalizado se você quiser um editor que trabalhe apenas com o seu tipo de projeto ou se você quiser um editor que tenha apenas alguns comandos específicos. Observe, no entanto, que os usuários não poderão [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usar um editor personalizado para editar projetos padrão.

 Um editor personalizado pode usar uma fábrica de editores e adicionar informações sobre o editor ao registro. No entanto, o tipo de projeto associado ao editor personalizado pode instanciar o editor personalizado de outras maneiras.

 Um editor personalizado pode usar ativação no local ou incorporação simplificada para implementar uma exibição.

### <a name="external-editors"></a>Editores externos
 Editores externos são editores que não estão integrados ao Visual Studio, como Microsoft Word, Notepad ou Microsoft FrontPage. Você pode chamar esse editor se, por exemplo, você estiver passando texto para ele a partir do seu VSPackage. Editores externos se registram e podem ser usados fora do Visual Studio. Quando você chama um editor externo, e ele pode ser incorporado em uma janela de host, então ele aparece em uma janela no IDE. Se não, então o IDE cria uma janela separada para ele.

 O <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> método define a prioridade <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> do documento usando a enumeração. Se `DP_External` o valor for especificado, o arquivo pode ser aberto por um editor externo.

## <a name="editor-design-decisions"></a>Decisões de design de editor
 As seguintes perguntas de design ajudarão você a escolher o tipo de editor mais adequado à sua aplicação:

- Seu aplicativo salvará seus dados em arquivos ou não? Se ele salvar seus dados em arquivos, eles estarão em um formato personalizado ou padrão?

   Se você usar um formato de arquivo padrão, outros tipos de projeto, além do seu projeto, poderão abrir e ler/gravar dados para eles. Se você usar um formato de arquivo personalizado, no entanto, apenas o tipo de projeto poderá abrir e ler/gravar dados para eles.

   Se o seu projeto usa arquivos, então você deve personalizar o editor padrão. Se o seu projeto não usar arquivos, mas usar itens em um banco de dados ou outro repositório, então você deve criar um editor personalizado.

- Seu editor precisa hospedar controles ActiveX?

   Se o editor hospeda controles ActiveX, implemente um editor de ativação no local, conforme descrito [na ativação in loco](/visualstudio/misc/in-place-activation?view=vs-2015). Se ele não hospedar controles ActiveX, use um editor de incorporação [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] simplificado ou personalize o editor padrão.

- Seu editor suportará várias visualizações? Você deve suportar vários visualizações se quiser que as visualizações do seu editor sejam visíveis ao mesmo tempo que o editor padrão.

   Se o seu editor precisar de suporte a várias visualizações, os dados do documento e os objetos de exibição de documentos para o editor devem ser objetos separados. Para obter mais informações, consulte [Suporte a várias exibições de documentos](../extensibility/supporting-multiple-document-views.md).

   Se o seu editor suportar várias visualizações, você planeja usar a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementação do buffer de texto do editor principal (objeto)<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> para o objeto de dados do documento? Ou seja, você deseja apoiar sua visão de editor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lado a lado com o editor principal? A capacidade de fazer isso é a base do designer de formulários..

- Se você precisar hospedar um editor externo, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]o editor pode ser incorporado dentro?

   Se ele puder ser incorporado, você deve criar uma janela <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> de host <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> para o `DP_External`editor externo e, em seguida, chamar o método e definir o valor de enumeração para . Se o editor não puder ser incorporado, o IDE criará automaticamente uma janela separada para ele.

## <a name="in-this-section"></a>Nesta seção

[Passo a passo: Crie um editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md)\
Explica como criar um editor personalizado.

[Passo a passo: Adicione recursos a um editor personalizado](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Explica como adicionar recursos a um editor personalizado.

[Inicialização do designer e configuração de metadados](../extensibility/designer-initialization-and-metadata-configuration.md)\
Explica como inicializar um designer.

[Suporte de desfazer de suprimentos para designers](../extensibility/supplying-undo-support-to-designers.md)\
Explica como fornecer suporte desfazer para designers.

[Colorir sintaxe em editores personalizados](../extensibility/syntax-coloring-in-custom-editors.md)\
Explica a diferença entre coloração de sintaxe no editor principal e em editores personalizados.

[Dados de documentos e visualização de documentos em editores personalizados](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Explica como implementar dados de documentos e visualizações de documentos em editores personalizados.

## <a name="related-sections"></a>Seções relacionadas

[Interfaces legadas no editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Explica como acessar o editor principal por meio da API herdada.

[Desenvolva um serviço de linguagem legado](../extensibility/internals/developing-a-legacy-language-service.md)\
Explica como implementar um serviço de idiomas.

[Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Explica como criar elementos de IU que correspondem ao resto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
