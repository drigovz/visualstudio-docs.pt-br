---
title: Fornecendo suporte aos Designers de desfazer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 87ddc0e21a3945ed522014b86174a578c04faa2e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095640"
---
# <a name="supply-undo-support-to-designers"></a>Fonte de suporte de desfazer para designers

Designers, editores, como o geralmente necessário dar suporte a operações de desfazer, para que os usuários podem reverter suas alterações recentes ao modificar um elemento de código.

A maioria dos designers implementados no Visual Studio tem suporte é fornecido automaticamente pelo ambiente de "Desfazer".

Implementações de designer que precisam para fornecer suporte para o recurso de desfazer:

- Fornecer gerenciamento de desfazer, Implementando a classe base abstrata <xref:System.ComponentModel.Design.UndoEngine>

- CodeDOM e persistência forneça suportam com a implementação de <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> classes.

Para obter mais informações sobre como escrever designers usando [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], consulte [estender o suporte de tempo de Design](/previous-versions/37899azc(v=vs.140)).

O [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornece uma infraestrutura de desfazer padrão por:

- Fornecendo implementações de gerenciamento por meio de desfazer a <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> e <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> classes.

- Fornecendo o suporte do CodeDOM através do padrão e persistência <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> e <xref:System.ComponentModel.Design.IComponentChangeService> implementações.

## <a name="obtain-undo-support-automatically"></a>Obter suporte à função desfazer automaticamente

Qualquer designer criado no Visual Studio tem suporte à função desfazer automática e completa se, o designer:

- Faz uso de um <xref:System.Windows.Forms.Control> com base em classe para sua interface do usuário.

- Emprega a geração de código padrão com base em CodeDOM e sistema de análise para persistência e geração de código.

   Para obter mais informações sobre como trabalhar com o suporte do CodeDOM do Visual Studio, consulte [geração dinâmica de código fonte e compilação](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Quando usar o suporte à função desfazer de Designer explícita
 Designers devem fornecer seu próprio gerenciamento de desfazer se eles usarem uma interface gráfica do usuário, conhecida como um adaptador de exibição, que não seja um fornecido pelo <xref:System.Windows.Forms.Control>.

 Um exemplo disso pode estar criando um produto com uma interface de design gráfico baseado na web em vez de um [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-com base em interface gráfica.

 Nesses casos, é necessário registrar esse adaptador de exibição com o Visual Studio usando <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>e fornecer gerenciamento explícito de desfazer.

 Designers precisam fornecer suportam de CodeDOM e persistência se eles não usarem o modelo de geração de código do Visual Studio fornecido no <xref:System.CodeDom> para nome.

## <a name="undo-support-features-of-the-designer"></a>Recursos de suporte do Designer de desfazer
 O SDK do ambiente fornece implementações padrão de interfaces necessárias para fornecer suporte que pode ser usado pelos designers não usando de desfazer <xref:System.Windows.Forms.Control> com base em classes para suas interfaces de usuário ou o modelo de CodeDOM e persistência padrão.

 O <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe deriva de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] <xref:System.ComponentModel.Design.UndoEngine> classe usando uma implementação do <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> classe para gerenciar operações de desfazer.

 O Visual Studio fornece o recurso a seguir para desfazer designer:

- Funcionalidade de desfazer vinculado entre vários designers.

- Unidades de filho dentro de um designer podem interagir com seus pais, implementando <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> em <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

O SDK do ambiente fornece suportam de CodeDOM e persistência, fornecendo:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> como uma implementação das <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Um <xref:System.ComponentModel.Design.IComponentChangeService> fornecida pelo host de design do Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Use os recursos do SDK de ambiente para fornecer suporte à função desfazer

Para obter suporte à função desfazer, um objeto que implementa um designer deve instanciar e inicializar uma instância das <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> classe com uma validade <xref:System.IServiceProvider> implementação. Isso <xref:System.IServiceProvider> classe deve fornecer os seguintes serviços:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Designers usando a serialização de CodeDOM do Visual Studio podem optar por usar <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> fornecido com o [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] como sua implementação do <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   Nesse caso, o <xref:System.IServiceProvider> classe fornecida para o <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> construtor deve retornar esse objeto como uma implementação do <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> classe.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Usando o padrão de designers <xref:System.ComponentModel.Design.DesignSurface> fornecida pelo design do Visual Studio host são garantidos para terem uma implementação padrão da <xref:System.ComponentModel.Design.IComponentChangeService> classe.

Designers de implementar um <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> desfazer com base mecanismo controla automaticamente as alterações se:

- As alterações de propriedade são feitas por meio de <xref:System.ComponentModel.TypeDescriptor> objeto.

- <xref:System.ComponentModel.Design.IComponentChangeService> eventos são gerados manualmente quando uma alteração que pode ser desfeita é confirmada.

- Modificação no designer foi criada dentro do contexto de um <xref:System.ComponentModel.Design.DesignerTransaction>.

- O designer escolhe criar unidades de desfazer usando explicitamente a unidade de desfazer padrão fornecida por uma implementação do <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> ou a implementação específica do Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, que é derivada de <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> e também fornece um implementação de ambos <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> e <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Estender o suporte de tempo de Design](/previous-versions/37899azc(v=vs.140))