---
title: Atualizar o Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, proteção, community edition, ofuscação, .NET, gratuito, Visual Studio 2019, Visual Studio 2017, Visual Studio, atualização,linha de comando
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: Saiba como atualizar a cópia gratuita do Dotfuscator Community, incluída no Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 78a26da7734e4fa74a9b312b41786caca4b7cc67
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652821"
---
# <a name="upgrade-dotfuscator-community"></a>Atualizar o Dotfuscator Community

O Dotfuscator Community oferece vários recursos de proteção e defesa, imediatamente, para o aplicativo para todos os desenvolvedores que usam o Microsoft Visual Studio.
No entanto, há mais recursos disponíveis aos usuários que atualizam a versão do Dotfuscator.

## <a name="registering-dotfuscator-community"></a>Registrando o Dotfuscator Community

Usuários registrados da Comunidade Dotfuscator obtêm acesso a recursos adicionais, como [suporte de linha de comando][cli], o que torna mais fácil integrar a Comunidade Dotfuscator ao seu processo de compilação automatizado. O registro também concede acesso a uma ferramenta interna usada para [decodificar rastreamentos de pilha ofuscados][decode-obfuscated].

O registro é rápido, simples e gratuito.
Para registrar a Comunidade do Dotfuscator, consulte [as instruções no guia completo do usuário da Comunidade Dotfuscator][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Embora o Dotfuscator Community forneça um nível básico de proteção, o ***PreEmptive Protection – Dotfuscator Professional*** inclui funcionalidades de proteção e transformação de ofuscação avançadas, tais como:

* *Proteção de propriedade intelectual*
  * Opções de renomeação avançadas, incluindo Enhanced Overload Induction™ e seleção de identificador aleatória.
  * Acesso a transformações de ofuscação de nível empresarial, incluindo [transformações destinadas a anular a descompilação de código automatizado][control-flow].
  * A capacidade de [obscurecer cadeias de caracteres confidenciais][string-encryption], tornando impossível uma pesquisa simples do código descompilado.
  * A capacidade de [Inserir discretamente a propriedade e as cadeias de caracteres de distribuição em seus assemblies][watermarking], permitindo que você determine a origem de vazamentos de software não autorizados.
  * A capacidade de [combinar vários assemblies em um][linking], tornando ainda mais difícil para os invasores determinarem as funções dos elementos de código, uma vez que a separação de preocupações foi eliminada.
  * A capacidade de [remover automaticamente o código não utilizado de seu aplicativo][pruning], reduzindo a quantidade de código confidencial enviado.
* *Proteção de integridade do aplicativo*
  * Comportamentos adicionais de [defesa do aplicativo][check-actions].
  * A capacidade de fornecer um período de aviso antes da data limite do fim da vida útil do aplicativo.
  * A capacidade de notificar o código do aplicativo durante um período de aviso do fim da vida útil ou após a data limite.

O Dotfuscator Professional é o [ofuscador .net][net-obfuscator] padrão da indústria e é adequado para os desenvolvedores corporativos que precisam de suporte contínuo, manutenção e atualizações de produtos.
Além disso, o Dotfuscator Professional oferece maior integração com o Visual Studio e é licenciado para uso comercial.

Para obter mais informações sobre os recursos avançados de proteção de aplicativo do Dotfuscator Professional, visite a [página de visão geral do Dotfuscator][product-about] da PreEmptive Solutions e [Compare-o à comunidade do Dotfuscator][product-compare].
As [avaliações com suporte total estão disponíveis em Preemptive.com][eval].

## <a name="see-also"></a>Consulte também

[Este artigo no guia do usuário completo da Comunidade Dotfuscator][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html