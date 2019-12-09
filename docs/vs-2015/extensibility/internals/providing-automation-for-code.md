---
title: Fornecer automação para código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e4d47a72adf787f5d560374e1c44743004d25f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203236"
---
# <a name="providing-automation-for-code"></a>Fornecendo automação de código
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Não é necessário criar um modelo de automação para seu código. O SDK do ambiente não fornece um exemplo para fazer isso. Para obter informações sobre modelos de código, consulte o <xref:EnvDTE.CodeModel> objeto.  
  
 Para implementar um modelo de código, você deve implementar quaisquer interfaces que são determinadas pela sua estrutura de dados interno. Os objetos devem ser derivados de `IDispatch` classe.  
  
 Os objetos que você estender, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, estão disponíveis no <xref:EnvDTE.Project> de objeto e a seguinte aparência:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 Você pode optar por implementar apenas a `CodeModel` ou o `FileCodeModel` interface no objeto de retorno de seu `Project` e <xref:EnvDTE.ProjectItem> objetos. Forneça qualquer funcionalidade dessa interface apropriada para seu sistema de projeto.  
  
 Se você quiser adicionar recursos, como métodos ou propriedades, que não estão disponíveis no padrão `CodeModel` e `FileCodeModel` interfaces, crie sua própria interface que herda do padrão. Certifique-se de documentá-lo com o seu sistema de projeto para que os usuários finais saibam procurá-lo. Você retorna a interface padrão, mas o usuário pode chamar o `QueryInterface` método ou a conversão em sua interface, se ela é conhecida por existir.  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral do modelo de automação](../../extensibility/internals/automation-model-overview.md)
