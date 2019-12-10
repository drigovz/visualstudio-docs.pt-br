---
title: Atualizador tem erros de recuperação de informações
description: Instruções de correção ao ver o erro "Erro ao recuperar informações de atualização". no Visual Studio 2019 para Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: b25285ff3060734ee18085d7a9e89cd0d0c43439
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984408"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Solução de problemas: o atualizador tem erros ao recuperar informações

Em raras ocasiões, você poderá ver a mensagem de erro "Erro ao recuperar informações de atualização" ao tentar [atualizar o Visual Studio para Mac](update.md). Se isso acontecer, tente as seguintes etapas para corrigi-lo:

- Verifique sua conexão com a Internet. Uma queda na conexão é a causa mais comum desse erro.
  - Se um componente falhar ao baixar, você pode clicar no botão Repetir ao lado do nome do componente para tentar baixá-lo novamente.
- Reinicie o IDE.
- Se você continuar a ver essa mensagem de erro, também é possível tentar atualizar usando o instalador se o **.dmg** ainda estiver no seu computador ou baixe-o em [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - O instalador atualizará todos os componentes instalados em seu computador.
  - Ao executar novamente o instalador, você também poderá instalar os componentes ausentes que não instalou anteriormente.
- Você também pode tentar limpar arquivos baixados em cache, excluindo o arquivo localizado em `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`.
