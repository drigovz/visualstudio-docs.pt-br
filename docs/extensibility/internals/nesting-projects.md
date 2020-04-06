---
title: Projetos de Aninhamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707028"
---
# <a name="nesting-projects"></a>Aninhando projetos
Os desenvolvedores de aplicativos corporativos que usam seu pacote [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VS podem agrupar convenientemente tipos semelhantes de projetos usando *o aninhamento de projetos*. Por exemplo, o projeto Enterprise Template usa projetos aninhados para agrupar projetos em categorias. Projetos de fachada de negócios, projetos de UI web e assim por diante são agrupados em uma categoria.

 Neste cenário, não há limite para o número de projetos que o desenvolvedor pode aninhar sob cada projeto pai, embora o desenvolvedor possa fornecer limites programáticamente. Esse tipo de agrupamento também pode ser feito recursivo, nesse caso os projetos do mesmo tipo de projeto infantil podem ser aninhados sob a criança para se tornar um subprojeto da criança, que é um subprojeto do pai.

 O ninho de projetos não é [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]uma parte intrínseca de . Você tem que escrever o código para permitir o aninhamento e o ninho de subprojetos dentro de projetos infantis. O projeto pai é um VSPackage especial, ou tipo de projeto, criado e registrado com seu próprio GUID que inclui o código necessário para implementar o ninho de projeto.

 Você pode encontrar um exemplo de como aninhar projetos no [Como: Implementar projetos aninhados](../../extensibility/internals/how-to-implement-nested-projects.md).

## <a name="nested-projects-example"></a>Exemplo de projetos aninhados
 ![Solução de projetos aninhados](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjetos") Exemplo de projetos aninhados

## <a name="see-also"></a>Confira também
- [Considerações para descarregar e recarregar projetos aninhados](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Suporte do assistente para projetos aninhados](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Registrando modelos de projeto e item](../../extensibility/internals/registering-project-and-item-templates.md)
- [Implementando a manipulação de comando para projetos aninhados](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrando a caixa de diálogo AddItem para projetos aninhados](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)
- [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
