---
title: Expondo tipos a designers visuais | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708431"
---
# <a name="expose-types-to-visual-designers"></a>Expor tipos a designers visuais
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve ter acesso às definições de classe e tipo em tempo de design para exibir um designer visual. As classes são carregadas de um conjunto predefinido de assemblies que incluem o conjunto de dependências completo do projeto atual (referências mais suas dependências). Também pode ser necessário que os designers visuais acessem classes e tipos definidos em arquivos gerados por ferramentas personalizadas.

 Os [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas de projeto e fornecem suporte para acessar classes e tipos gerados por meio de arquivos executáveis portáteis temporários (PES temporários). Qualquer arquivo gerado por uma ferramenta personalizada pode ser compilado em um assembly temporário para que os tipos possam ser carregados a partir desses assemblies e expostos aos designers. A saída de cada ferramenta personalizada é compilada em um PE temporário separado, e o êxito ou a falha dessa compilação temporária depende apenas de se o arquivo gerado pode ou não ser compilado. Embora um projeto não possa compilar como um todo, o PEs temporário individual ainda pode estar disponível para os designers.

 O sistema de projeto fornece suporte completo para controlar alterações no arquivo de saída de uma ferramenta personalizada, desde que essas alterações sejam o resultado da execução da ferramenta personalizada. Cada vez que a ferramenta personalizada é executada, um novo PE temporário é gerado e as notificações apropriadas são enviadas aos designers.

> [!NOTE]
> Como o arquivo de geração executável do programa temporário ocorre em segundo plano, nenhum erro será relatado ao usuário se a compilação falhar.

 As ferramentas personalizadas que tiram proveito do suporte a PE temporário devem seguir as seguintes regras:

- **GeneratesDesignTimeSource** deve ser definido como 1 no registro.

     Não ocorre uma compilação de arquivo executável de programa sem essa configuração.

- O código gerado deve estar no mesmo idioma que a configuração do projeto global.

     O PE temporário é compilado independentemente do que a ferramenta personalizada relata como a extensão solicitada no <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> desde que **GeneratesDesignTimeSource** esteja definido como 1 no registro. A extensão não precisa ser *. vb*, *. cs*ou *. jsl*; pode ser qualquer extensão.

- O código gerado pela ferramenta personalizada deve ser válido e deve ser compilado por conta própria usando apenas o conjunto de referências presentes no projeto no momento em que a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> execução é concluída.

     Quando um PE temporário é compilado, o único arquivo de origem fornecido ao compilador é a saída da ferramenta personalizada. Portanto, uma ferramenta personalizada que usa um PE temporário deve gerar arquivos de saída que podem ser compilados independentemente de outros arquivos no projeto.

## <a name="see-also"></a>Confira também
- [Introdução ao objeto BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementar geradores de arquivo único](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrar geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md)
