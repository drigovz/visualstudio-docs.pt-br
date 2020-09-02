---
title: Estendendo a caixa de ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- tools [Visual Studio], Toolbox
- Toolbox [Visual Studio SDK]
ms.assetid: bb84a79e-cd4c-4a58-8871-2513e7119b6e
caps.latest.revision: 38
manager: jillfra
ms.openlocfilehash: ddf67fba3ae603dbd31d4628c61a6f14cc2441c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686940"
---
# <a name="extending-the-toolbox"></a>Estendendo a caixa de ferramentas
A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **caixa de ferramentas** fornece uma coleção de objetos que fornecem funcionalidade a editores e designers por meio do mecanismo de arrastar e soltar do IDE.  
  
 Há duas maneiras básicas em que um VSPackage funciona com a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **caixa de ferramentas**:  
  
- Um VSPackage pode adicionar novos itens de dados e controles à **caixa de ferramentas**.  
  
- Um VSPackage pode ser um destino ou consumidor de funcionalidade de **caixa de ferramentas** existente, dando suporte às operações de arrastar e soltar e configurando a aparência da caixa de **ferramentas**.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como criar um controle de caixa de ferramentas que usa o Windows Forms](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md)  
 Descreve como criar um controle de caixa de ferramentas usando o modelo de controle de caixa de ferramentas Windows Forms.  
  
 [Criar um controle de caixa de ferramentas do WPF](../extensibility/creating-a-wpf-toolbox-control.md)  
 Descreve como criar um controle de caixa de ferramentas usando o modelo de controle de caixa de ferramentas do WPF.  
  
 [Gerenciando a caixa de ferramentas](../misc/managing-the-toolbox.md)  
 Descreve como um VSPackage pode gerenciar o conteúdo e a aparência da **caixa de ferramentas**.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Como gerenciar a janela Caixa de Ferramentas](https://msdn.microsoft.com/a022c3fe-298c-4a59-a48f-b050da90ebc2)  
 Descreve como trabalhar com a **caixa de ferramentas** no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE).  
  
 [Como controlar a Caixa de Ferramentas](https://msdn.microsoft.com/library/c9d8a18a-d2bc-43d4-a803-601bfc6a6599)  
 Descreve como gerenciar a **caixa de ferramentas** usando o modelo de programação de automação.  
  
 [Estender outras partes do Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Explica como usar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] os serviços do para criar elementos de interface do usuário que correspondam ao restante do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .