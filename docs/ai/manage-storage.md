---
title: Procurar armazenamento para carregar dados
description: Saiba como você pode procurar todo o armazenamento no computador remoto ou no compartilhamento de arquivos do Azure para habilitar o carregamento de dados ou o download de modelos e logs.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: ae419c67b493ef03b08f6fcf627ad0fbe42ca6d0
ms.sourcegitcommit: 9c57730000d5ced37d3887f3928b17076f49d0f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2020
ms.locfileid: "92099200"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procurar no armazenamento para carregar dados ou baixar modelos e logs

É possível procurar em todo o armazenamento no computador remoto ou no compartilhamento de arquivos do Azure para habilitar o upload de dados ou download de modelos e logs. Ou, se desejar acessar os logs e as saídas de trabalho de um trabalho específico, você poderá fazer isso também no navegador do trabalho.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para acessar todos os dados no computador remoto ou no compartilhamento de arquivos

1. Abra o **Gerenciador de servidores**.
2. Expanda o computador remoto ou o contexto de computação do IA do Lote.
3. Clique com o botão direito do mouse em **Armazenamento** e, em seguida, clique em **Procurar**.

    ![armazenamento](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acessar dados específicos do trabalho no computador remoto ou no compartilhamento de arquivos

1. Abra o [Histórico de Trabalhos](job-details.md)
2. Selecione o trabalho.
3. Clique em **pasta de trabalho** ou clique em **stdout/stderr** para ter acesso rápido a esses arquivos de log importantes.

    ![armazenamento](media/manage-storage/job-workingfolder.png)
