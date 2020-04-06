---
title: Fornecimento de suporte de desfazer para designers | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699668"
---
# <a name="supply-undo-support-to-designers"></a>Suporte de desfazer de suprimentos para designers

Designers, como editores, normalmente precisam suportar operações desfazer para que os usuários possam reverter suas alterações recentes ao modificar um elemento de código.

A maioria dos designers implementados no Visual Studio tem suporte "desfazer" fornecido automaticamente pelo ambiente.

Implementações de designer que precisam fornecer suporte para o recurso de desfazer:

- Fornecer gerenciamento desfazer implementando a classe base abstrata<xref:System.ComponentModel.Design.UndoEngine>

- Persistência de fornecimento e suporte ao <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> CodeDOM implementando as classes e <xref:System.ComponentModel.Design.IComponentChangeService> as classes.

Para obter mais informações sobre como escrever designers usando o .NET Framework, consulte [Extend Design-Time Support](/previous-versions/37899azc(v=vs.140)).

O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece uma infra-estrutura padrão de desfazer por:

- Fornecendo implementações de <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> gestão <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> desfazer através das aulas e das aulas.

- Fornecendo persistência e suporte ao CodeDOM através da inadimplência <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> implementações.

## <a name="obtain-undo-support-automatically"></a>Obtenha desfazer suporte automaticamente

Qualquer designer criado no Visual Studio tem suporte automático e completo de desfazer se, o designer:

- Faz uso <xref:System.Windows.Forms.Control> de uma classe baseada para sua interface de usuário.

- Emprega o sistema padrão de geração e análise de código baseado em CodeDOM para geração e persistência de código.

   Para obter mais informações sobre como trabalhar com suporte ao Visual Studio CodeDOM, consulte [Dynamic Source Code Generation and Compilation](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usar o suporte explícito de desfazer o designer
 Os designers devem fornecer seu próprio gerenciamento de desfazer se usarem uma interface gráfica <xref:System.Windows.Forms.Control>do usuário, referida como um adaptador de exibição, diferente do fornecido por .

 Um exemplo disso pode ser criar um produto com uma interface de design gráfico baseada na Web em vez de uma interface gráfica baseada em .NET Framework.

 Nesses casos, seria necessário registrar este adaptador de <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>visualização com o Visual Studio usando , e fornecer gerenciamento explícito de desfazer.

 Os designers precisam fornecer codedom e suporte de persistência se não usarem <xref:System.CodeDom> o modelo de geração de código visual studio fornecido no espaço de nome.

## <a name="undo-support-features-of-the-designer"></a>Desfazer recursos de suporte do designer
 O Ambiente SDK fornece implementações padrão de interfaces necessárias para fornecer <xref:System.Windows.Forms.Control> suporte desfeito que pode ser usado por designers que não usam classes baseadas para suas interfaces de usuário ou o codedom padrão e modelo de persistência.

 A <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva da classe <xref:System.ComponentModel.Design.UndoEngine> .NET Framework <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> usando uma implementação da classe para gerenciar operações de desfazer.

 O Visual Studio fornece o seguinte recurso para desfazer o designer:

- Funcionalidade desvinculada vinculada em vários designers.

- As unidades infantis dentro de um designer <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> podem <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>interagir com seus pais implementando e assim por diante .

O SDK de meio ambiente fornece suporte ao CodeDOM e persistência fornecendo:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>como uma implementação do<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Um <xref:System.ComponentModel.Design.IComponentChangeService> fornecido pelo apresentador de design visual studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Use os recursos do SDK do ambiente para fornecer suporte de desfazer

Para obter suporte desfazer, um objeto que implemente um <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> designer deve <xref:System.IServiceProvider> instanciar e inicializar uma instância da classe com uma implementação válida. Esta <xref:System.IServiceProvider> classe deve fornecer os seguintes serviços:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Os designers que utilizam a serialização <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> do Visual [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Studio CodeDOM <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>podem optar por usar como sua implementação do .

   Neste caso, <xref:System.IServiceProvider> a classe fornecida <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> ao construtor deve devolver esse <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> objeto como uma implementação da classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Os designers <xref:System.ComponentModel.Design.DesignSurface> que usam o padrão fornecido pelo host de design <xref:System.ComponentModel.Design.IComponentChangeService> Visual Studio têm a garantia de ter uma implementação padrão da classe.

Os designers <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> que implementam um mecanismo de desfazer baseado rastreiam automaticamente as alterações se:

- Alterações de propriedade <xref:System.ComponentModel.TypeDescriptor> são feitas através do objeto.

- <xref:System.ComponentModel.Design.IComponentChangeService>eventos são gerados manualmente quando uma alteração indodável é cometida.

- A modificação no designer foi criada <xref:System.ComponentModel.Design.DesignerTransaction>no contexto de um .

- O designer opta por criar explicitamente unidades desfazer usando a unidade <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> padrão de desfazer fornecida por <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> uma implementação ou <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>a implementação <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>específica do Visual Studio, que deriva e também fornece uma implementação de ambos e .

## <a name="see-also"></a>Confira também

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Estender o suporte ao tempo de projeto](/previous-versions/37899azc(v=vs.140))
