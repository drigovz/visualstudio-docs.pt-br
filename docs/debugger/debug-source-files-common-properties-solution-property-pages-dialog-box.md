---
title: Depurar arquivos de origem/páginas de propriedades da solução
description: Acesse a página de propriedades depurar arquivos de origem no Visual Studio clicando com o botão direito do mouse em sua solução em Gerenciador de Soluções e selecionando Propriedades > Propriedades comuns.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 10818f473dec392364832cdc2f5215197ef4627f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873165"
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedades da Solução
Esta página de propriedades especifica onde o depurador procurará arquivos de origem ao depurar a solução.

 Para acessar a página de propriedades **Depurar Arquivos de Origem**, clique com o botão direito do mouse na solução em **Gerenciador de Soluções** e selecione **Propriedades** no menu de atalho. Expanda a pasta **Propriedades Comuns** e clique na página **Depurar Arquivos de Origem**.

 **Diretórios que contêm o código-fonte** Contém uma lista de diretórios nos quais o depurador pesquisa arquivos de origem ao depurar a solução. Os subdiretórios dos diretórios especificados também são pesquisados.

 **Não procurar esses arquivos de origem** Insira os nomes dos arquivos que você não deseja que o depurador Leia. Se o depurador encontrar um desses arquivos em um dos diretórios especificados acima, ele o ignorará. Se a caixa de diálogo **Localizar Fonte** aparecer durante a depuração e você clicar em **Cancelar**, o arquivo que você procurava será adicionado a essa lista para que o depurador não continue a procurar o arquivo.

## <a name="see-also"></a>Confira também

- [Segurança do depurador](../debugger/debugger-security.md)
- [Configurações e preparação do depurador](../debugger/debugger-settings-and-preparation.md)