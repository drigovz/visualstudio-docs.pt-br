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
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cee876a3904d5c47b43b58793087c901e8444dd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557236"
---
# <a name="upgrade-dotfuscator-community"></a>Atualizar o Dotfuscator Community

O Dotfuscator Community oferece vários recursos de proteção e defesa, imediatamente, para o aplicativo para todos os desenvolvedores que usam o Microsoft Visual Studio.
No entanto, há mais recursos disponíveis aos usuários que atualizam a versão do Dotfuscator.

## <a name="registering-dotfuscator-community"></a>Registrando o Dotfuscator Community

Os usuários registrados do Dotfuscator Community obtêm acesso a recursos adicionais, como [suporte a linha de comando][cli], o que facilita a integração do Dotfuscator Community ao processo de build automatizado. Além disso, o registro concede acesso à ferramenta incorporada, usada para [decodificar rastreamentos de pilha ocultados][decode-obfuscated].

O registro é rápido, simples e gratuito.
Para registrar o Dotfuscator Community, confira [as instruções no Guia completo do usuário do Dotfuscator Community][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Embora o Dotfuscator Community forneça um nível básico de proteção, o ***PreEmptive Protection – Dotfuscator Professional*** inclui funcionalidades de proteção e transformação de ofuscação avançadas, tais como:

* *Proteção de propriedade intelectual*
  * Opções de renomeação avançadas, incluindo Enhanced Overload Induction™ e seleção de identificador aleatória.
  * Acesso a transformações de ofuscação de nível empresarial, incluindo [transformações destinadas a acabar com a descompilação automatizada de código][control-flow].
  * A capacidade de [obscurecer cadeias de caracteres confidenciais][string-encryption], impossibilitando uma pesquisa simples do código descompilado.
  * A capacidade de [inserir discretamente cadeias de caracteres de propriedade e de distribuição nos assemblies][watermarking], permitindo determinar a origem de perdas de software não autorizadas.
  * A capacidade de [combinar vários assemblies em um][linking], tornando ainda mais difícil para invasores determinar as funções de elementos de código, pois a separação de preocupações foi eliminada.
  * A capacidade de [remover automaticamente o código não utilizado do aplicativo][pruning], reduzindo a quantidade de código confidencial fornecido.
* *Proteção de integridade do aplicativo*
  * [Comportamentos de defesa do aplicativo][check-actions] adicionais.
  * A capacidade de fornecer um período de aviso antes da data limite do fim da vida útil do aplicativo.
  * A capacidade de notificar o código do aplicativo durante um período de aviso do fim da vida útil ou após a data limite.

O Dotfuscator Professional é o [.NET Obfuscator][net-obfuscator] padrão do setor e é adequado para desenvolvedores empresariais que precisam de atualizações de produto, manutenção e suporte contínuos.
Além disso, o Dotfuscator Professional oferece maior integração com o Visual Studio e é licenciado para uso comercial.

Para obter mais informações sobre os recursos avançados de proteção para o aplicativo do Dotfuscator Professional, visite a [página da Visão geral do Dotfuscator][product-about] da PreEmptive Solutions e [faça uma comparação com o Dotfuscator Community][product-compare].
[Avaliações com suporte completo estão disponíveis em preemptive.com][eval].

## <a name="see-also"></a>Consulte também

[Este artigo no Guia completo do usuário do Dotfuscator Community][full]

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