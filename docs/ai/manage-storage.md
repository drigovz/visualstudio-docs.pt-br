---
title: Procurar armazenamento para carregar dados
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 7d0f2522117f4c5a5b85e99e2779d10cffcb7f22
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777405"
---
# <a name="browse-storage-to-upload-data-or-download-models-and-logs"></a>Procurar no armazenamento para carregar dados ou baixar modelos e logs

É possível procurar em todo o armazenamento no computador remoto ou no compartilhamento de arquivos do Azure para habilitar o upload de dados ou download de modelos e logs. Ou, se desejar acessar os logs e as saídas de trabalho de um trabalho específico, você poderá fazer isso também no navegador do trabalho.

## <a name="to-access-all-data-on-the-remote-machine-or-file-share"></a>Para acessar todos os dados no computador remoto ou no compartilhamento de arquivos

1. Abra o **Gerenciador de Servidores**.
2. Expanda o computador remoto ou o contexto de computação do IA do Lote.
3. Clique com o botão direito do mouse em **Armazenamento** e, em seguida, clique em **Procurar**.

    ![storage](media/manage-storage/browse-storage.png)

## <a name="to-access-job-specific-data-on-the-remote-machine-or-file-share"></a>Para acessar dados específicos do trabalho no computador remoto ou no compartilhamento de arquivos

1. Abra o [Histórico de Trabalhos](job-details.md)
2. Selecione o trabalho.
3. Clique em **Pasta de Trabalho** ou clique em **StdOut / Stderr** para acesso rápido a esses importantes arquivos de log.

    ![storage](media/manage-storage/job-workingfolder.png)
