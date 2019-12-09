---
title: Caixa de diálogo Configurações Internacionais, Ambiente, Opções
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e55c0e81877c2735571705a2b2d2529b0fa3a74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666998"
---
# <a name="options-dialog-box-environment--international-settings"></a>Caixa de diálogo opções: ambiente \> configurações internacionais

A página Configurações Internacionais permite alterar o idioma padrão quando você tem mais de uma versão de idioma do IDE (ambiente de desenvolvimento integrado) instalada em seu computador. Você pode acessar essa caixa de diálogo selecionando **Opções** no menu **Ferramentas** e, em seguida, escolhendo **Configurações Internacionais** na pasta **Ambiente**.

**Linguagem**

Lista os idiomas disponíveis para as versões de idioma do produto instalado. Se vários idiomas de produtos ou uma instalação de idioma misto dos produtos compartilhar o ambiente, a seleção de idioma será alterada para **Usar o idioma do Microsoft Windows**.

> [!CAUTION]
> Em um sistema com vários idiomas instalados, as ferramentas de build do Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e arquivos relacionados) não são afetadas por essa configuração. Essas ferramentas usam a versão do último idioma instalado. As ferramentas de build do idioma instalado anteriormente são substituídas porque as ferramentas de build do Visual C++ não usam o modelo DLL satélite.

### <a name="see-also"></a>Consulte também

- [Instalar pacotes de idiomas](../../install/install-visual-studio.md#step-6---install-language-packs-optional)