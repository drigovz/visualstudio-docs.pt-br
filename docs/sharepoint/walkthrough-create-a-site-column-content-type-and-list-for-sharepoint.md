---
title: Criar coluna de site, tipo de conteúdo e lista para SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.GeneralMessageHelp
- Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping
- VS.SharePointTools.ListDesigner.SortingGrouping
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, list definitions
- SharePoint development in Visual Studio, list instances
- SharePoint development in Visual Studio, fields
- SharePoint development in Visual Studio, content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e78594a98066dec6cedff6da6f3f1de823bec796
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985012"
---
# <a name="walkthrough-create-a-site-column-content-type-and-list-for-sharepoint"></a>Walkthrough: criar uma coluna de site, um tipo de conteúdo e uma lista para o SharePoint
  Os procedimentos a seguir demonstram como criar colunas de site do SharePoint (ou *campos*) personalizados, bem como um tipo de conteúdo que usa as colunas do site. Ele também mostra como criar uma lista que usa o novo tipo de conteúdo.

 Esta explicação passo a passo inclui as seguintes tarefas:

- [Crie colunas de site personalizadas](#create-custom-site-columns).

- [Crie um tipo de conteúdo personalizado](#create-a-custom-content-type).

- [Crie uma lista](#create-a-list).

- [Teste o aplicativo](#test-the-application).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- Edições com suporte do Windows e do SharePoint.

- [!INCLUDE[vsprvs-current](../sharepoint/includes/vsprvs-current-md.md)]

## <a name="create-custom-site-columns"></a>Criar colunas de site personalizadas
 Este exemplo cria uma lista para gerenciar pacientes em um hospital. Primeiro, você deve criar um projeto do SharePoint no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e adicionar colunas do site a ele, da seguinte maneira.

#### <a name="to-create-the-project"></a>Para criar o projeto

1. No menu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **arquivo** , escolha **novo** **projeto**de > .

2. Na caixa de diálogo **novo projeto** , em **Visual C#**  ou **Visual Basic**, expanda o nó **SharePoint** e, em seguida, escolha **2010**.

3. No painel **modelos** , escolha **projeto do SharePoint 2010**, altere o nome do projeto para **clínica**e, em seguida, escolha o botão **OK** .

     O modelo de projeto do SharePoint 2010 é um projeto vazio que é usado neste exemplo para conter colunas de site e outros itens de projeto que são adicionados posteriormente.

4. Na página **especificar o site e o nível de segurança para depuração** , insira a URL do site do SharePoint local ao qual você deseja adicionar o novo item de campo personalizado ou use o local padrão (`http://<``>/)`do *sistema* .

5. Na seção **o que é o nível de confiança para esta solução do SharePoint?** , use o valor padrão **implantar como uma solução de área restrita**.

     Para obter mais informações sobre soluções de farm e área restrita, consulte [Considerações sobre a solução em área restrita](../sharepoint/sandboxed-solution-considerations.md).

6. Escolha o botão **concluir** . Agora, o projeto está listado em **Gerenciador de soluções**.

#### <a name="to-add-site-columns"></a>Para adicionar colunas de site

1. Adicione uma nova coluna de site. Para fazer isso, em **Gerenciador de soluções**, abra o menu de atalho para a **clínica**e, em seguida, escolha **Adicionar** > **novo item**.

2. Na caixa de diálogo **Adicionar novo item** , escolha **coluna do site**, altere o nome para **nome do paciente**e, em seguida, escolha o botão **Adicionar** .

3. No arquivo *Elements. xml* da coluna do site, deixe a configuração de **tipo** como **texto**e altere a configuração de **grupo** para colunas do **site de clínica**. Ao concluir, o arquivo *Elements. xml* da coluna do site deve ser semelhante ao exemplo a seguir.

    ```xml
    <Field
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"
         Name="Clinic - Patient Name"
         DisplayName="Patient Name"
         Type="Text"
         Required="FALSE"
         Group="Clinic Site Columns">
    </Field>
    ```

4. Usando o mesmo procedimento, adicione mais duas colunas do site ao projeto: **ID do paciente** (tipo = "inteiro") e **nome do doutor** (tipo = "texto"). Defina o valor do grupo como **colunas do site da clínica**.

## <a name="create-a-custom-content-type"></a>Criar um tipo de conteúdo personalizado
 Em seguida, crie um tipo de conteúdo — com base no tipo de conteúdo contatos — que inclui as colunas do site que você criou no procedimento anterior. Com base em um tipo de conteúdo em um tipo de conteúdo existente, você pode economizar tempo, pois o tipo de conteúdo base fornece várias colunas de site para uso no novo tipo de conteúdo.

#### <a name="to-create-a-custom-content-type"></a>Para criar um tipo de conteúdo personalizado

1. Adicione um tipo de conteúdo ao projeto. Para fazer isso, em **Gerenciador de soluções**, escolha o nó do projeto

2. Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.

3. Em **Visual C#**  ou **Visual Basic**, expanda o nó do **SharePoint** e escolha o nó **2010** .

4. No painel **modelos** , escolha o modelo de **tipo de conteúdo** , altere o nome para informações do **paciente**e, em seguida, escolha o botão **Adicionar** .

     O **Assistente para personalização do SharePoint** é aberto.

5. Em **qual tipo de conteúdo base esse tipo de conteúdo deve herdar da** lista, escolha **contato** como o tipo de conteúdo no qual basear o novo tipo de conteúdo e, em seguida, escolha o botão **concluir** .

     Isso lhe dá acesso a outras colunas de site potencialmente úteis no tipo de conteúdo de contato, além das colunas de site que você definiu anteriormente.

6. Depois que o designer de tipo de conteúdo for exibido, na guia **colunas** , adicione as três colunas do site que você definiu anteriormente: **nome do paciente**, **ID do paciente**e nome do **médico**. Para adicionar essas colunas, escolha a primeira caixa de listagem na lista colunas do site em **nome de exibição**e escolha cada coluna do site na lista, uma de cada vez.

    > [!TIP]
    > Para escolher as colunas do site mais rapidamente, filtre a lista inserindo as primeiras letras do nome da coluna.

7. Além das três colunas de site personalizadas, adicione a coluna site de **comentários** da lista colunas do site.

8. Marque a caixa de seleção **necessário** para as colunas **nome do paciente** e site da **ID do paciente** para torná-las campos obrigatórios.

9. Na guia **tipo de conteúdo** , verifique se o nome do tipo de conteúdo é **informações sobre o paciente**e altere a descrição para o cartão de informações do **paciente**.

10. Altere o **nome do grupo** para os tipos de conteúdo da **clínica**e deixe as outras configurações com seus valores padrão.

11. Na barra de menus, escolha **arquivo** > **salvar tudo**e, em seguida, feche o designer de tipo de conteúdo.

## <a name="create-a-list"></a>Criar uma lista
 Agora, crie uma lista que usa o novo tipo de conteúdo e colunas de site.

#### <a name="to-create-a-list"></a>Para criar uma lista

1. Adicione uma lista ao projeto. Para fazer isso, em **Gerenciador de soluções**, escolha o nó do projeto.

2. Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.

3. Em **Visual C#**  ou **Visual Basic**, expanda o nó do **SharePoint** e escolha o nó **2010** .

4. No painel **modelos** , escolha o modelo de **lista** , altere o nome para **pacientes**e, em seguida, escolha o botão **Adicionar** .

5. Deixe a opção **Personalizar a lista com base na** configuração como **padrão (em branco)** e escolha o botão **concluir** .

6. No designer de lista, escolha o botão **tipos de conteúdo** para exibir a caixa de diálogo Configurações de tipo de **conteúdo** .

7. Escolha a nova linha, escolha o tipo de conteúdo **informações do paciente** na lista de tipos de conteúdo e escolha o botão **OK** .

     Isso adiciona todas as colunas do site do tipo de conteúdo **informações do paciente** à lista.

8. Exclua todas as colunas do site na lista, exceto as seguintes:

    - ID do paciente

    - Nome do paciente

    - Telefone residencial

    - Mensagens

    - Nome do doutor

    - Comentários

9. Em **nome de exibição da coluna**, escolha uma linha vazia, adicione uma coluna de lista personalizada e nomeie-a como **hospital**. Deixe seu tipo de dados como **uma linha de texto**.

     A coluna de lista personalizada aplica-se somente a essa lista. Quando você adiciona uma coluna de lista personalizada a uma lista, um novo tipo de conteúdo de lista, incluindo todas as colunas adicionadas à lista, é criado e definido como a lista padrão.

    > [!TIP]
    > Se você escolher uma coluna na lista de colunas do site, uma coluna de site existente será usada. No entanto, se você inserir um valor de nome de coluna sem escolher colunas na lista, uma coluna de lista personalizada será criada, mesmo que uma coluna com o mesmo nome já exista na lista.

     Opcionalmente, em vez de definir o tipo de dados para a coluna de lista personalizada como **uma única linha de texto**, você pode definir o tipo de dados para essa coluna como Lookup e seus valores seriam recuperados de uma tabela ou de outra lista. Para obter informações sobre colunas de pesquisa, consulte [relações de lista no SharePoint 2010](/previous-versions/msp-n-p/ff798514(v=pandp.10)) e [pesquisas e relações de lista](/previous-versions/office/developer/sharepoint-2010/ff623048(v=office.14)).

10. Ao lado das caixas **ID do paciente** e nome do **paciente** , marque a caixa de seleção **necessário** .

11. Na guia **exibições** , escolha uma linha vazia para criar uma exibição. Insira os **detalhes do paciente**.

     Na guia **modos de exibição** , você pode especificar as colunas que deseja que apareçam na lista do SharePoint.

12. Escolha a linha novos **detalhes do paciente** e, em seguida, escolha o botão **definir como padrão** .

     A nova exibição agora é a exibição padrão da lista.

13. Adicione as seguintes colunas à lista **colunas selecionadas** na seguinte ordem:

    - ID do paciente

    - Nome do paciente

    - Telefone residencial

    - Mensagens

    - Nome do doutor

    - Hospital

    - Comentários

14. Na lista **Propriedades** , escolha a propriedade **classificar e agrupar** e, em seguida, escolha o ![ícone](../sharepoint/media/ellipsisicon.gif "Ícone de reticências") de reticências botão de reticências para exibir a caixa de diálogo **classificar e agrupar** .

15. Na lista **nome da coluna** , escolha **nome do paciente**, verifique se a coluna de **classificação** está definida como **crescente**e, em seguida, escolha o botão **OK** .

## <a name="test-the-application"></a>Testar o aplicativo
 Agora que as colunas de site personalizadas, o tipo de conteúdo e a lista estão prontos, implante-as no SharePoint e execute o aplicativo para testá-lo.

#### <a name="to-test-the-application"></a>Para testar o aplicativo

1. Na barra de menus, escolha **Arquivo** > **Salvar Todos**.

2. Escolha a tecla **F5** para executar o aplicativo.

     O aplicativo é compilado e, em seguida, seus recursos são implantados no SharePoint e ativados.

3. Na barra de navegação rápida, escolha o link **pacientes** para exibir a lista de **pacientes** .

     Os nomes de coluna na lista devem corresponder aos que você inseriu na guia **modos de exibição** em [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

4. Escolha o link **Adicionar novo item** para criar um cartão de informações do paciente.

5. Insira informações nos campos e, em seguida, escolha o botão **salvar** .

     O novo registro aparece na lista.

## <a name="see-also"></a>Consulte também
- [Criar colunas de site, tipos de conteúdo e listas para o SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)
- [Desenvolver soluções do SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Como: criar um tipo de campo personalizado](/previous-versions/office/developer/sharepoint-2010/bb862248(v=office.14))
- [Tipos de conteúdo](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14))
- [Columns](/previous-versions/office/developer/sharepoint-2010/ms196085(v=office.14))
