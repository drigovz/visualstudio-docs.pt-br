---
title: Obtendo informações de serviço da Loja de Configurações | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b15d5c9f122ca66d21940b9998969b0d39d1a74d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711369"
---
# <a name="get-service-information-from-the-settings-store"></a>Obtenha informações de serviço na loja de configurações
Você pode usar a loja de configurações para encontrar todos os serviços disponíveis ou para determinar se um determinado serviço está instalado. Você deve saber o tipo de classe de serviço.

## <a name="to-list-the-available-services"></a>Para listar os serviços disponíveis

1. Crie um projeto `FindServicesExtension` VSIX nomeado e `FindServicesCommand`adicione um comando personalizado chamado . Para obter mais informações sobre como criar um comando personalizado, consulte [Criar uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Em *FindServicesCommand.cs,* adicione as seguintes diretivas usando:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    using System.Windows.Forms;
    ```

3. Obtenha o armazenamento de configurações e encontre a subcoleção chamada Services. Esta coleção inclui todos os serviços disponíveis. No `MenuItemCommand` método, remova o código existente e substitua-o pelo seguinte:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string message = "Available services:\n";
        IEnumerable<string> collection = configurationSettingsStore.GetSubCollectionNames("Services");
        int n = 0;
        foreach (string service in collection)
        {
            message += configurationSettingsStore.GetString("Services\\" + service, "Name", "Unknown") + "\n";
        }

        MessageBox.Show(message);
    }
    ```

4. Compile o projeto e comece a depuração. A instância experimental aparece.

5. Na instância experimental, no menu **Ferramentas,** clique em **Invocar FindServicesCommand**.

     Você deve ver uma caixa de mensagens listando todos os serviços.

     Para verificar essas configurações, você pode usar o editor do registro.

## <a name="find-a-specific-service"></a>Encontre um serviço específico
 Você também pode <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> usar o método para determinar se um determinado serviço está instalado. Você deve saber o tipo de classe de serviço.

1. No MenuItemCallback do projeto que você criou no procedimento anterior, pesquise na loja de configurações a `Services` coleção que tem a subcoleção nomeada pelo GUID do serviço. Neste caso, procuraremos o serviço de Ajuda.

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
        string helpServiceGUID = typeof(SVsHelpService).GUID.ToString("B").ToUpper();
        bool hasHelpService = configurationSettingsStore.CollectionExists("Services\\" + helpServiceGUID);
        string message = "Help Service Available: " + hasHelpService;

        MessageBox.Show(message);
    }
    ```

2. Compile o projeto e comece a depuração.

3. Na instância experimental, no menu **Ferramentas,** clique em **Invocar FindServicesCommand**.

     Você deve ver uma mensagem com o texto **Serviço de ajuda disponível:** seguido por **True** ou **False**. Para verificar essa configuração, você pode usar um editor de registro, como mostrado nas etapas anteriores.
