---
title: Visão geral das soluções
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767db749d953855cd5c6f81f356a195c830aa838
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705306"
---
# <a name="solutions-overview"></a>Visão geral das soluções

Uma solução é um agrupamento de um ou mais projetos que trabalham juntos para criar um aplicativo. As informações de projeto e status relativas à solução são armazenadas em dois arquivos de solução diferentes. O [arquivo solution (.sln)](solution-dot-sln-file.md) é baseado em texto e pode ser colocado sob controle de código fonte e compartilhado entre os usuários. O [arquivo de opção de usuário de solução (.suo)](solution-user-options-dot-suo-file.md) é binário. Como resultado, o arquivo .suo não pode ser colocado sob controle de código fonte e contém informações específicas do usuário.

Qualquer VSPackage pode gravar para qualquer tipo de arquivo de solução. Devido à natureza dos arquivos, existem duas interfaces diferentes implementadas para escrever para eles. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> interface grava informações de texto para <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> o arquivo .sln e a interface grava fluxos binários para o arquivo .suo.

> [!NOTE]
> Um projeto não precisa escrever explicitamente uma entrada para si mesmo no arquivo de solução; o ambiente lida com isso para o projeto. Portanto, a menos que você queira adicionar conteúdo adicional especificamente ao arquivo de solução, você não precisa registrar seu VSPackage desta forma.

Cada solução de suporte ao VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> usa três interfaces, a interface, que é `IVsPersistSolutionProps` `IVsPersistSolutionOpts`implementada pelo ambiente e chamada pelo VSPackage, e, ambas implementadas pelo VSPackage. A `IVsPersistSolutionOpts` interface só precisa ser implementada se as informações privadas forem escritas pelo VSPackage para o arquivo .suo.

Quando uma solução é aberta, o seguinte processo ocorre.

1. O ambiente lê a solução.

2. Se o ambiente `CLSID`encontrar um, ele carrega o VSPackage correspondente.

3. Se um VSPackage estiver carregado, `QueryInterface` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> o ambiente exige interface para a interface que o VSPackage requer.

   - Ao ler a partir de um arquivo `QueryInterface` `IVsPersistSolutionProps`.sln, o ambiente solicita .

   - Ao ler a partir de um arquivo `QueryInterface` `IVsPersistSolutionOpts`.suo, o ambiente solicita .

   Informações específicas relacionadas ao uso desses arquivos podem ser encontradas na [Solução (. SLn)](../../extensibility/internals/solution-dot-sln-file.md) Opções de usuário de arquivo e [solução (. Suo) Arquivo](../../extensibility/internals/solution-user-options-dot-suo-file.md).

> [!NOTE]
> Se você quiser criar uma nova configuração de solução que consiste em configurações de dois projetos e excluir um terço da compilação, você precisa usar a im do Property Pages ou a automação. Você não pode alterar as configurações do gerenciador de compilação de soluções e suas propriedades diretamente, mas você pode manipular o gerenciador de compilação de soluções usando a `SolutionBuild` classe do DTE no modelo de automação. Para obter mais informações sobre a configuração de soluções, consulte [Configuração da solução](../../extensibility/internals/solution-configuration.md).

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
