---
title: Funcionalidades do Dotfuscator
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, proteção, community edition, ofuscação, .NET, gratuito, Visual Studio 2017, Visual Studio 2019, Visual Studio
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator Community
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
description: Conheça as funcionalidades da cópia gratuita do Dotfuscator Community, incluída no Visual Studio 2017.
ms.assetid: 0ee89c58-c900-48fc-a6a2-65ace00e8bab
author: Joe-Sewell-PreEmptive
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 249c039070246f27669f3a808cf607a649db1e59
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747936"
---
# <a name="capabilities-of-dotfuscator"></a>Funcionalidades do Dotfuscator

Esta página enfoca os recursos da Comunidade Dotfuscator com algumas referências a opções avançadas disponíveis por meio de [atualizações][upgrades].

O Dotfuscator Community é um sistema *pós-build* para aplicativos .NET.
Com ele, os usuários do Visual Studio podem [ofuscar os assemblies][obfuscation] e injetar [medidas de defesa ativa][checks] no aplicativo, tudo sem Dotfuscator precisarem acessar o código-fonte original.
O Dotfuscator protege seu aplicativo de várias maneiras, criando uma estratégia de proteção em camadas.

A Comunidade Dotfuscator dá suporte a uma ampla variedade de tipos de aplicativos e assembly .NET, incluindo [plataforma universal do Windows (UWP)][uwp] e [Xamarin][xamarin].

## <a name="intellectual-property-protection"></a>Proteção de propriedade intelectual

O design, o comportamento e a implementação do aplicativo são formas de IP (propriedade intelectual).
No entanto, os aplicativos criados para o .NET são essencialmente abertos. é fácil fazer a engenharia reversa de assemblies .NET, [pois eles contêm metadados de alto nível e código intermediário][assemblies].

A Comunidade Dotfuscator inclui [ofuscação][obfuscation] básica de .net na forma de [renomeação][renaming].
A ofuscação do código com o Dotfuscator reduz o risco de acesso não autorizado ao código-fonte por meio de engenharia reversa, já que informações importantes de nomenclatura deixarão de ser públicas.
A ofuscação também mostra um esforço de sua parte em proteger o código contra o exame – uma etapa importante em estabelecer que sua IP é legalmente protegida como segredo comercial.

Muitos dos [recursos de proteção de integridade do aplicativo](#application-integrity-protection) do Dotfuscator Community impedem ainda mais a engenharia reversa.
Por exemplo, um ator mal-intencionado pode tentar anexar um depurador a uma instância em execução do aplicativo para entender a lógica do programa.
O Dotfuscator pode injetar o [comportamento de antidepuração][debug] em seu aplicativo para obstruir isso.

## <a name="application-integrity-protection"></a>Proteção de integridade do aplicativo

Além de proteger o código-fonte, também é importante garantir que o aplicativo seja usado como projetado.
Os invasores podem tentar sequestrar o aplicativo para contornar políticas de licenciamento (ou seja, pirataria de software), roubar ou manipular dados confidenciais tratados pelo aplicativo ou alterar o comportamento do aplicativo.

A Comunidade Dotfuscator pode injetar [código de validação de aplicativo][checks] em seus assemblies, incluindo medidas de dispositivo [antiadulteração][tamper], [antidepuração][debug]e [com raiz][root] .
Quando um estado de aplicativo inválido é detectado, o código de validação pode [ser chamado no código do aplicativo para tratar a situação de forma apropriada][check-app].
Ou, se você preferir não escrever código para lidar com usos inválidos do aplicativo, o Dotfuscator também poderá injetar comportamentos de [resposta][check-action] , sem a necessidade de qualquer modificação no código-fonte.

Muitos desses mesmos métodos também podem ser usados para impor [prazos de fim de vida][shelflife] para avaliação ou software de avaliação.

## <a name="see-also"></a>Consulte também

[Este tópico no Guia completo do usuário do Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[assemblies]:  https://docs.microsoft.com/dotnet/standard/assembly-format
[uwp]:  https://www.preemptive.com/blog/article/856-uwp-applications-in-dotfuscator-ce/91-dotfuscator-ce
[xamarin]:  https://www.preemptive.com/obfuscating-xamarin-with-dotfuscator

[upgrades]:  upgrades.md

[obfuscation]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_overview.html
[renaming]:  https://www.preemptive.com/dotfuscator/ce/docs/help/obfuscation_renaming.html

[checks]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html
[check-app]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#app-notification
[check-action]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_overview.html#action

[tamper]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_tamper.html
[debug]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_debug.html
[root]: https://www.preemptive.com/dotfuscator/ce/docs/help/checks_root.html
[shelflife]:  https://www.preemptive.com/dotfuscator/ce/docs/help/checks_shelflife.html

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_capabilities.html
