---
title: Resolvendo assemblies em tempo de design| Microsoft Docs
description: Saiba como o MSBuild resolve referências a assemblies em tempo de design usando assemblies de referência no pacote de direcionamento.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f7927ff370ab05f4931cb0346f00f65157a411d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937921"
---
# <a name="resolve-assemblies-at-design-time"></a>Resolver assemblies em tempo de design

Quando você adiciona uma referência a um assembly por meio da guia **.NET** da caixa de diálogo **Adicionar Referência**, a referência aponta para um assembly de referência intermediário ou seja, um assembly que contém todas as informações de tipo e a assinatura, mas que não necessariamente contém qualquer código. A guia **.net** lista os assemblies de referência que correspondem aos assemblies de tempo de execução no .NET Framework. Além disso, ela lista os assemblies de referência que correspondem aos assemblies de runtime nas pastas AssemblyFoldersEx registradas que são usados por terceiros.

## <a name="multi-targeting"></a>Multiplataforma

 O Visual Studio permite que você direcione versões do .NET Framework que são executadas em várias versões do .NET Framework. Quando uma nova versão do .NET Framework for lançada, a estrutura poderá ser instalada usando um pacote de direcionamento e será mostrada automaticamente como um destino no Visual Studio.

## <a name="how-type-resolution-works"></a>Como funciona a resolução de tipo

 Em tempo de execução, o CLR resolve os tipos no assembly procurando no GAC, no diretório *bin* e em quaisquer caminhos de investigação. Isso é manipulado pelo carregador de fusão. Mas como o carregador de fusão sabe o que está procurando? Isso depende de uma resolução feita no tempo de design, quando o aplicativo é compilado.

 Durante o build, o compilador resolve tipos de aplicativos usando os assemblies de referência. Nas versões 2.0, 3.0, 3.5, 4, 4.5 e 4.5.1 do .NET Framework, os assemblies de referência são instalados quando o .NET Framework é instalado.

 Os assemblies de referência são fornecidos pelo pacote de direcionamento que acompanha a versão correspondente do SDK do .NET Framework. O Framework em si fornece apenas os assemblies de runtime. Para compilar aplicativos, você precisa instalar o .NET Framework e o SDK do .NET Framework correspondente.

 Quando você usa como destino um .NET Framework específico, o sistema de build resolve todos os tipos usando os assemblies de referência no pacote de destino. Em tempo de execução, o carregador de fusão resolve esses mesmos tipos para os assemblies de tempo de execução, que normalmente estão localizados no GAC.

 Se os assemblies de referência não estiverem disponíveis, o sistema de build resolverá tipos do assembly usando os assemblies de runtime. Já que os assemblies de runtime no GAC não são diferenciados por números de versão secundária, é possível que a resolução seja feita para o assembly errado. Isso poderá ocorrer, por exemplo, se um novo método introduzido no .NET Framework versão 3.5 for referenciado enquanto a versão 3.0 for usada como destino. O build será bem-sucedido e o aplicativo será executado no computador do build, mas falhará quando implantado em um computador que não tenha a versão 3.5 instalada.

 O pacote de direcionamento que agora é fornecido com o SDK do .NET Framework inclui uma lista de todos os assemblies de runtime nessa versão do Framework, denominada lista de redistribuição (redist), impossibilitando ao sistema de build resolver tipos contra a versão errada do assembly.

## <a name="see-also"></a>Confira também
- [Conceitos avançados](../msbuild/msbuild-advanced-concepts.md)
