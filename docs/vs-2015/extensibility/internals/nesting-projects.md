---
title: Aninhando projetos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e3a0fae42dc7bf1497e3d0d4a9d23f9cab50675
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "68180427"
---
# <a name="nesting-projects"></a>Aninhando projetos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Os desenvolvedores de aplicativos empresariais que usam o pacote do VS podem, de forma conveniente, agrupar tipos semelhantes de projetos em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usando o *aninhamento de projetos*. Por exemplo, o projeto de modelo empresarial usa projetos aninhados para agrupar projetos em categorias. Projetos de fachada de negócios, projetos de interface do usuário da Web e assim por diante são agrupados em uma categoria.  
  
 Nesse cenário, não há nenhum limite para o número de projetos que o desenvolvedor pode aninhar em cada projeto pai, embora o desenvolvedor possa fornecer limites programaticamente. Esse tipo de agrupamento também pode ser recursivo, caso em que os projetos do mesmo tipo que um projeto filho podem ser aninhados sob o filho para se tornar um subprojeto do filho, que é um subprojeto do pai.  
  
 O aninhamento de projetos não é uma parte intrínseca do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Você precisa escrever o código para habilitar o aninhamento e aninhamento de subprojetos em projetos filho. O projeto pai é um VSPackage especial, ou tipo de projeto, criado e registrado com seu próprio GUID que inclui o código necessário para implementar o aninhamento de projetos.  
  
 Você pode encontrar um exemplo de projetos aninhados no C# exemplo de projeto aninhado.  
  
## <a name="nested-projects-example"></a>Exemplo de projetos aninhados  
 (../../extensibility/internals/media/vsnestedprojects.gif "VsNestedProjects") de ![solução de projetos aninhados]  
Exemplo de projetos aninhados  
  
## <a name="see-also"></a>Consulte também  
 [Como implementar projetos aninhados](../../extensibility/internals/how-to-implement-nested-projects.md)   
 [Considerações para descarregar e recarregar projetos aninhados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)   
 [Suporte do assistente para projetos aninhados](../../extensibility/internals/wizard-support-for-nested-projects.md)   
 [Registrando modelos de projeto e Item](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Implementando manipulação de comandos para projetos aninhados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)   
 [Filtrando a caixa de diálogo AddItem para projetos aninhados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)   
 [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)   
 [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
