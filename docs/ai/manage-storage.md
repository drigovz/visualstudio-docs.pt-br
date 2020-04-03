---
title: Procurar armazenamento para carregar dados
author: jillre
ms.author: jillfra
manager: jillfra
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: ece3ffa3a273e903f403fd7df7005bfb54172f62
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638451"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procurar no armazenamento para carregar dados ou baixar modelos e logs

É possível procurar em todo o armazenamento no computador remoto ou no compartilhamento de arquivos do Azure para habilitar o upload de dados ou download de modelos e logs. Ou, se desejar acessar os logs e as saídas de trabalho de um trabalho específico, você poderá fazer isso também no navegador do trabalho.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para acessar todos os dados no computador remoto ou no compartilhamento de arquivos

1. Abra o **Server Explorer**.
2. Expanda o computador remoto ou o contexto de computação do IA do Lote.
3. Clique com o botão direito do mouse em **Armazenamento** e, em seguida, clique em **Procurar**.

    ![armazenamento](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acessar dados específicos do trabalho no computador remoto ou no compartilhamento de arquivos

1. Abra o [Histórico de Trabalhos](job-details.md)
2. Selecione o trabalho.
3. Clique **em Working Folder** ou clique em **StdOut / Stderr** para acesso rápido a esses arquivos de log importantes.

    ![armazenamento](media/manage-storage/job-workingfolder.png)
