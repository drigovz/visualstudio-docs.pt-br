---
title: Configurações internacionais na caixa de diálogo opções
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1210f217c9e1dc1f8a90eb99fec9e55970aa8eff
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102487"
---
# <a name="options-dialog-box-environment--international-settings"></a>Caixa de diálogo opções: \> configurações internacionais de ambiente

A página Configurações Internacionais permite alterar o idioma padrão quando você tem mais de uma versão de idioma do IDE (ambiente de desenvolvimento integrado) instalada em seu computador. Você pode acessar essa caixa de diálogo selecionando **Opções** no menu **Ferramentas** e, em seguida, escolhendo **Configurações Internacionais** na pasta **Ambiente** .

**Idioma**

Lista os idiomas disponíveis para as versões de idioma do produto instalado. Se vários idiomas de produtos ou uma instalação de idioma misto dos produtos compartilhar o ambiente, a seleção de idioma será alterada para **Usar o idioma do Microsoft Windows** .

> [!CAUTION]
> Em um sistema com vários idiomas instalados, as ferramentas de build do Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e arquivos relacionados) não são afetadas por essa configuração. Essas ferramentas usam a versão do último idioma instalado. As ferramentas de build do idioma instalado anteriormente são substituídas porque as ferramentas de build do Visual C++ não usam o modelo DLL satélite.

### <a name="see-also"></a>Veja também

- [Instalar pacote de idiomas](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
