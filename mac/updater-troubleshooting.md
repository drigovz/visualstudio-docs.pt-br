---
title: Atualizador tem erros de recuperação de informações
description: Instruções de correção ao ver o erro "Erro ao recuperar informações de atualização". no Visual Studio 2019 para Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75405475"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Solução de problemas: o atualizador tem erros ao recuperar informações

Em raras ocasiões, você poderá ver a mensagem de erro "Erro ao recuperar informações de atualização" ao tentar [atualizar o Visual Studio para Mac](update.md). Se isso acontecer, tente as seguintes etapas para corrigi-lo:

- Verifique sua conexão com a Internet. Uma queda na conexão é a causa mais comum desse erro.
  - Se um componente falhar ao baixar, você pode clicar no botão Repetir ao lado do nome do componente para tentar baixá-lo novamente.
- Reinicie o IDE.
- Se você continuar a ver essa mensagem de erro, também é possível tentar atualizar usando o instalador se o **.dmg** ainda estiver no seu computador ou baixe-o em [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - O instalador atualizará todos os componentes instalados em seu computador.
  - Ao executar novamente o instalador, você também poderá instalar os componentes ausentes que não instalou anteriormente.
- Você também pode tentar limpar arquivos baixados em cache, excluindo o arquivo localizado em `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`.
- Se estiver trabalhando com uma versão mais antiga do Visual Studio para Mac, você poderá ter outros números de versão no diretório `VisualStudio`. Exclua o arquivo de `index.xml` nesses caminhos também.
