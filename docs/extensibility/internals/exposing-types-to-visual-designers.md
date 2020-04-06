---
title: Expondo Tipos a Designers Visuais | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708431"
---
# <a name="expose-types-to-visual-designers"></a>Expor tipos a designers visuais
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]deve ter acesso a definições de classe e tipo na hora do design, a fim de exibir um designer visual. As classes são carregadas a partir de um conjunto predefinido de conjuntos que incluem o conjunto completo de dependência do projeto atual (referências mais suas dependências). Também pode ser necessário que os designers visuais acessem classes e tipos definidos em arquivos gerados por ferramentas personalizadas.

 Os [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas e os projetos fornecem suporte para acessar classes e tipos gerados por meio de arquivos executáveis portáteis temporários (PEs temporários). Qualquer arquivo gerado por uma ferramenta personalizada pode ser compilado em uma montagem temporária para que os tipos possam ser carregados desses conjuntos e expostos a designers. A saída de cada ferramenta personalizada é compilada em um PE temporário separado, e o sucesso ou falha desta compilação temporária depende apenas se o arquivo gerado pode ou não ser compilado. Mesmo que um projeto possa não ser construído como um todo, os PEs temporários individuais ainda podem estar disponíveis para os designers.

 O sistema do projeto fornece suporte total para rastrear alterações no arquivo de saída de uma ferramenta personalizada, desde que essas alterações sejam o resultado da execução da ferramenta personalizada. Cada vez que a ferramenta personalizada é executada, um novo PE temporário é gerado e notificações apropriadas são enviadas aos designers.

> [!NOTE]
> Como o arquivo de geração executável do programa temporário acontece em segundo plano, nenhum erro é relatado ao usuário se a compilação falhar.

 As ferramentas personalizadas que aproveitam o suporte temporário de PE devem seguir as seguintes regras:

- **GeneratesDesignTimeSource** deve ser definido como 1 no registro.

     Nenhuma compilação de arquivo executável do programa ocorre sem essa configuração.

- O código gerado deve estar no mesmo idioma que a configuração global do projeto.

     O PE temporário é compilado independentemente do que a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> ferramenta personalizada reporte como a extensão solicitada no desde que **o GeneratesDesignTimeSource** seja definido como 1 no registro. A extensão não precisa ser *.vb,* *.cs*ou *.jsl;* pode ser qualquer extensão.

- O código gerado pela ferramenta personalizada deve ser válido, e deve ser compilado por conta própria <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> usando apenas o conjunto de referências presentes no projeto no momento em que termina a execução.

     Quando um PE temporário é compilado, o único arquivo de origem fornecido ao compilador é a saída de ferramenta personalizada. Portanto, uma ferramenta personalizada que usa um PE temporário deve gerar arquivos de saída que podem ser compilados independentemente de outros arquivos do projeto.

## <a name="see-also"></a>Confira também
- [Introdução ao objeto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementar geradores de arquivos únicos](../../extensibility/internals/implementing-single-file-generators.md)
- [Registre geradores de arquivos únicos](../../extensibility/internals/registering-single-file-generators.md)
