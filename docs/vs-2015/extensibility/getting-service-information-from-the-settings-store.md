---
title: Obtendo informações de serviço do repositório de configurações | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 7028d440-d16d-4b08-9b94-eb8cc93b25fc
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cfe754203ae9b4e951de5beef8cd829f9d7716bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204306"
---
# <a name="getting-service-information-from-the-settings-store"></a>Obtendo informações sobre o serviço por meio do repositório de configurações
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode usar o repositório de configurações para localizar todos os serviços disponíveis ou para determinar se um serviço específico está instalado. Você deve saber o tipo da classe de serviço.  
  
### <a name="to-list-the-available-services"></a>Para listar os serviços disponíveis  
  
1. Crie um projeto VSIX chamado FindServicesExtension e, em seguida, adicione um comando personalizado chamado FindServicesCommand. Para obter mais informações sobre como criar um comando personalizado, consulte [criando uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. No FindServicesCommand.cs, adicione as seguintes instruções using:  
  
    ```vb  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    using System.Windows.Forms;  
    ```  
  
3. Obtenha o repositório de definições de configuração e, em seguida, localize a subcoleção denominada serviços. Essa coleção inclui todos os serviços disponíveis. No método MenuItemCommand, remova o código existente e substitua-o pelo seguinte:  
  
    ```  
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
  
4. Compile o projeto e comece a depuração. A instância experimental é exibida.  
  
5. Na instância experimental, no menu **ferramentas** , clique em **invocar FindServicesCommand**.  
  
     Você deverá ver uma caixa de mensagem listando todos os serviços.  
  
     Para verificar essas configurações, você pode usar o editor do registro.  
  
## <a name="finding-a-specific-service"></a>Localizando um serviço específico  
 Você também pode usar o <xref:Microsoft.VisualStudio.Settings.SettingsStore.CollectionExists%2A> método para determinar se um serviço específico está instalado. Você deve saber o tipo da classe de serviço.  
  
1. No MenuItemCallback do projeto que você criou no procedimento anterior, pesquise o repositório de definições de configuração para a `Services` coleção que tem a subcoleção denominada pelo GUID do serviço. Nesse caso, procuraremos o serviço de ajuda.  
  
    ```  
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
  
3. Na instância experimental, no menu **ferramentas** , clique em **invocar FindServicesCommand**.  
  
     Você verá uma mensagem com o serviço de **ajuda de texto disponível:**  seguido por **true** ou **false**. Para verificar essa configuração, você pode usar um editor do registro, conforme mostrado nas etapas anteriores.
