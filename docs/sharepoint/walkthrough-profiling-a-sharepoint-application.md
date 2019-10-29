---
title: 'Walkthrough: criando perfil de um aplicativo do SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d001edcd281a0c21d244704f0a068850804b8762
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981152"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Walkthrough: criar perfil de um aplicativo do SharePoint
  Este tutorial mostra como usar as ferramentas de criação de perfil no Visual Studio para otimizar o desempenho de um aplicativo do SharePoint. O aplicativo de exemplo é um receptor de evento de recurso do SharePoint que contém um loop ocioso que degrada o desempenho do receptor de evento de recurso. O criador de perfil do Visual Studio permite que você localize e elimine a parte mais cara (com desempenho mais lento) do projeto, também conhecida como o *caminho quente*.

 Este tutorial demonstra as seguintes tarefas:

- [Addg um receptor de evento e](#add-a-feature-and-feature-event-receiver)recurso.

- [Configure e implante o aplicativo do SharePoint](#configure-and-deploy-the-sharepoint-application).

- [Execute o aplicativo do SharePoint](#run-the-sharepoint-application).

- [Exibir e interpretar os resultados do perfil](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Edições com suporte do Microsoft Windows e do SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]

## <a name="create-a-sharepoint-project"></a>Criar um projeto do SharePoint
 Primeiro, crie um projeto do SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Para criar um projeto do SharePoint

1. Na barra de menus, escolha **arquivo**  > **novo** **projeto** de  >  para exibir a caixa de diálogo **novo projeto** .

2. Expanda o nó do **SharePoint** sob o  **C# Visual** ou **Visual Basic**e escolha o nó **2010** .

3. No painel modelos, escolha o modelo de **projeto do SharePoint 2010** .

4. Na caixa **nome** , digite **ProfileTest**e, em seguida, escolha o botão **OK** .

    O **Assistente para personalização do SharePoint** é exibido.

5. Na página **especificar o site e o nível de segurança para depuração** , insira a URL para o site do SharePoint Server em que você deseja depurar a definição do site ou use o local padrão (<em>nome do sistema</em>http:///).

6. Na seção **o que é o nível de confiança para esta solução do SharePoint?** , escolha o botão de opção **implantar como uma solução de farm** .

    No momento, você só pode criar o perfil de soluções de farm. Para obter mais informações sobre soluções em área restrita versus soluções de farm, consulte [Considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).

7. Escolha o botão **concluir** . O projeto aparece no **Gerenciador de soluções**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Adicionar um receptor de evento de recurso e recurso
 Em seguida, adicione um recurso ao projeto junto com um receptor de evento para o recurso. Esse receptor de evento conterá o código a ser criado para o perfil.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Para adicionar um receptor de eventos de recurso e recurso

1. No **Gerenciador de soluções**, abra o menu de atalho para o nó **recursos** , escolha **Adicionar recurso**e deixe o nome no valor padrão, **Feature1**.

2. No **Gerenciador de soluções**, abra o menu de atalho para **Feature1**e escolha **Adicionar receptor de eventos**.

     Isso adiciona um arquivo de código ao recurso com vários manipuladores de eventos comentados e abre o arquivo para edição.

3. Na classe receptor de evento, adicione as seguintes declarações de variável.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. Substitua o procedimento `FeatureActivated` pelo código a seguir.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try
    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. Adicione o procedimento a seguir abaixo do procedimento de `FeatureActivated`.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. No **Gerenciador de soluções**, abra o menu de atalho do projeto (**ProfileTest**) e escolha **Propriedades**.

7. Na caixa de diálogo **Propriedades** , escolha a guia **SharePoint** .

8. Na lista **configuração de implantação ativa** , escolha **sem ativação**.

     A seleção dessa configuração de implantação permite que você ative manualmente o recurso mais tarde no SharePoint.

9. Salvar o projeto.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Configurar e implantar o aplicativo do SharePoint
 Agora que o projeto do SharePoint está pronto, configure-o e implante-o no servidor do SharePoint.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Para configurar e implantar o aplicativo do SharePoint

1. No menu **analisar** , escolha **Iniciar assistente de desempenho**.

2. Na página um do **Assistente de desempenho**, deixe o método de criação de perfil como **amostragem de CPU** e escolha o botão **Avançar** .

     Os outros métodos de criação de perfil podem ser usados em situações de criação de perfil mais avançadas. Para obter mais informações, consulte [Noções Básicas sobre Métodos de Coleta de Desempenho](/visualstudio/profiling/understanding-performance-collection-methods).

3. Na página dois do **Assistente de desempenho**, deixe o destino do perfil como **ProfileTest** e escolha o botão **Avançar** .

     Se uma solução tiver vários projetos, eles aparecerão nessa lista.

4. Na página três do **Assistente de desempenho**, desmarque a caixa de seleção **Habilitar criação de perfil de interação de camada** e, em seguida, escolha o botão **Avançar** .

     O recurso TIP (criação de perfil de interação de camada) é útil para medir o desempenho de aplicativos que consultam bancos de dados e mostrar o número de vezes que uma página da Web é solicitada. Como esses dados não são necessários para este exemplo, não Habilitaremos esse recurso.

5. Na página quatro do **Assistente de desempenho**, deixe a caixa de seleção **Iniciar criação de perfil após o assistente ser concluído** e escolha o botão **concluir** .

     O assistente habilita a criação de perfil de aplicativo no servidor, exibe a janela de **Gerenciador de desempenho** e, em seguida, compila, implanta e executa o aplicativo do SharePoint.

## <a name="run-the-sharepoint-application"></a>Executar o aplicativo do SharePoint
 Ative o recurso no SharePoint, disparando o código do evento `FeatureActivation` a ser executado.

### <a name="to-run-the-sharepoint-application"></a>Para executar o aplicativo do SharePoint

1. No SharePoint, abra o menu **ações do site** e, em seguida, escolha configurações do **site**.

2. Na lista **ações do site** , escolha o link **gerenciar recursos do site** .

3. Na lista de **recursos** , escolha o botão **Ativar** ao lado de **ProfileTest Feature1**.

     Há uma pausa quando você faz isso, devido ao loop ocioso sendo chamado na função `FeatureActivated`.

4. Na barra **início rápido** , escolha **listas** e, em seguida, na lista **listas** , escolha **anúncios**.

     Observe que um novo comunicado foi adicionado à lista informando que o recurso foi ativado.

5. Feche o site do SharePoint.

     Depois de fechar o SharePoint, o criador de perfil cria e exibe um exemplo de relatório de criação de perfil e o salva como um arquivo. vsp na pasta do projeto **ProfileTest** .

## <a name="view-and-interpret-the-profile-results"></a>Exibir e interpretar os resultados do perfil
 Agora que você executou e criou o perfil do aplicativo do SharePoint, exiba os resultados do teste.

### <a name="to-view-and-interpret-the-profile-results"></a>Para exibir e interpretar os resultados do perfil

1. Na seção **funções fazendo o mais individual** do relatório de criação de perfil de exemplo, observe que `TimeCounter` está próximo da parte superior da lista.

     Esse local indica que `TimeCounter` foi uma das funções com o maior número de amostras, o que significa que se trata de um dos maiores afunilamentos de desempenho no aplicativo. No entanto, essa situação não é surpreendente porque foi projetada de forma intencional para fins de demonstração.

2. Na seção **funções fazendo o trabalho mais individual** , escolha o link `ProcessRequest` para exibir a distribuição de custo para a função `ProcessRequest`.

     Na seção **funções chamadas** para `ProcessRequest`, observe que a função **FeatureActiviated** está listada como a função chamada mais cara.

3. Na seção **funções chamadas** , escolha o botão **FeatureActivated** .

     Na seção **funções chamadas** para **FeatureActivated**, a função `TimeCounter` é listada como a função chamada mais cara. No painel **exibição de código de função** , o código realçado (`TimeCounter`) é o ponto de interativação e indica onde a correção é necessária.

4. Feche o relatório de criação de perfil de exemplo.

     Para exibir o relatório novamente a qualquer momento, abra o arquivo. vsp na janela **Gerenciador de desempenho** .

## <a name="fix-the-code-and-reprofile-the-application"></a>Corrigir o código e recriar o perfil do aplicativo
 Agora que a função de HotSpot no aplicativo do SharePoint foi identificada, corrija-a.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Para corrigir o código e recriar o perfil do aplicativo

1. No código do receptor de evento de recurso, comente a chamada do método `TimeCounter` em `FeatureActivated` para impedir que ela seja chamada.

2. Salvar o projeto.

3. No **Gerenciador de desempenho**, abra a pasta destinos e escolha o nó **ProfileTest** .

4. Na barra de ferramentas **Gerenciador de desempenho** , na guia **ações** , escolha o botão **Iniciar criação de perfil** .

     Se você quiser alterar qualquer uma das propriedades de criação de perfil antes de reprofiling o aplicativo, escolha o botão **Assistente de inicialização de desempenho** em vez disso.

5. Siga as instruções na seção **executando o aplicativo do SharePoint** , anteriormente neste tópico.

     O recurso deve ser ativado muito mais rapidamente agora que a chamada para o loop ocioso foi eliminada. O relatório de criação de perfil de exemplo deve refletir isso.

## <a name="see-also"></a>Consulte também
- [Gerenciador de Desempenho](/visualstudio/profiling/performance-explorer)
- [Visão geral da sessão de desempenho](/visualstudio/profiling/performance-session-overview)
- [Guia do iniciante à criação de perfil de desempenho](/visualstudio/profiling/beginners-guide-to-performance-profiling)
- [Encontre afunilamentos de aplicativos com o criador de perfil do Visual Studio](https://msdn.microsoft.com/magazine/cc337887.aspx)
