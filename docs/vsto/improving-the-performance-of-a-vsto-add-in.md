---
title: Melhore o desempenho de um complemento VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416543"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Melhore o desempenho de um complemento VSTO
  Você pode dar aos seus usuários uma melhor experiência otimizando os complementos vsto que você cria para aplicativos do Office para que eles iniciem rapidamente, desliguem, abram itens e realizem outras tarefas. Se o seu Complemento VSTO for para o Outlook, você também pode reduzir a chance de que seu Add-in VSTO seja desativado devido ao desempenho ruim. Você pode aumentar o desempenho do seu Complemento VSTO implementando as seguintes estratégias:

- [Carregar complementos VSTO demanda](#Load).

- [Publicar soluções do Office usando o Windows Installer](#Publish).

- [Reflexo da fita de bypass](#Bypass).

- [Realize operações caras em um segmento de execução separado](#Perform).

  Para obter mais informações sobre como otimizar um complemento do Outlook VSTO, consulte critérios de [desempenho para manter os Complementos VSTO ativados](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>Carregar complementos VSTO demanda
 Você pode configurar um complemento VSTO para carregar somente nas seguintes circunstâncias:

- A primeira vez que o usuário inicia o aplicativo após a instalação do Complemento VSTO.

- A primeira vez que o usuário interage com o Complemento VSTO após iniciar o aplicativo a qualquer momento subsequente.

  Por exemplo, o complemento do VSTO pode preencher uma planilha com dados quando o usuário escolhe um botão personalizado que está rotulado **como Get My Data**. O aplicativo deve carregar seu Complemento VSTO pelo menos uma vez para que o botão **Obter meus dados** possa aparecer na Fita. No entanto, o Add-in VSTO não é carregado novamente quando o usuário inicia o aplicativo da próxima vez. O complemento DO VSTO só é carregado quando o usuário escolhe o botão **Obter meus dados.**

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar uma solução ClickOnce para carregar add-ins VSTO demanda

1. No **Solution Explorer,** escolha o nó do projeto.

2. Na barra de menu, escolha **Exibir** > **páginas de propriedade**.

3. Na guia **Publicar,** escolha o botão **Opções.**

4. Na caixa de diálogo **'Publicar opções',** escolha o item **'Configurações do escritório',** escolha a opção **Carregar em demanda** e escolha o botão **OK'.**

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Para configurar uma solução do Windows Installer para carregar add-ins VSTO demanda

1. No registro, defina `LoadBehavior` a entrada da chave ** _Root_\Software\Microsoft\Office\\_ApplicationName_\Addins\\Add-in ID** para **0x10**.

     Para obter mais informações, consulte [inscrições de Registro para Add-ins VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Para configurar uma solução para carregar add-ins VSTO demanda enquanto você depura a solução

1. Criar um script `LoadBehavior` que define a entrada da chave ** _Root_\\\Software\Microsoft\Office_ApplicationName_\Addins\\Add-in ID** to **0x10**.

     O código a seguir mostra um exemplo deste script.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Crie um evento pós-compilação que atualize o registro usando o script.

     O código a seguir mostra um exemplo de uma seqüência de comando que você pode adicionar a um evento pós-compilação.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Para obter informações sobre como criar um evento pós-construção em um projeto C#, consulte [Como: Especificar eventos de construção &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Para obter informações sobre como criar um evento pós-construção em um projeto Visual Basic, consulte [Como: Especificar eventos de construção &#40;&#41;Visual Basic ](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Publicar soluções do Office usando o Windows Installer
 Se você publicar sua solução usando o Windows Installer, o Visual Studio 2010 Tools for Office runtime contorna as seguintes etapas quando o Complemento VSTO é carregado.

- Validação do esquema manifesto.

- Verificando automaticamente se há atualizações.

- Validando as assinaturas digitais dos manifestos de implantação.

  > [!NOTE]
  > Essa abordagem não é necessária se você implantar seu Complemento VSTO em um local seguro nos computadores dos usuários.

  Para obter mais informações, consulte [Implantar uma solução do Office usando o Windows Installer](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>Reflexo da fita de bypass
 Se você criar uma [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]solução usando, certifique-se de que seus usuários instalaram a versão mais recente do Visual Studio 2010 Tools for Office runtime quando você implantar a solução. Versões mais antigas do tempo de execução do VSTO refletidas em conjuntos de soluções para localizar personalizações ribbon. Esse processo pode fazer com que o complemento vsto seja carregado mais lentamente.

 Como alternativa, você pode impedir que qualquer versão do Visual Studio 2010 Tools for Office use reflexão para identificar personalizações ribbon. Para seguir essa estratégia, `CreateRibbonExtensibility` anule o método e devolva explicitamente objetos Ribbon. Se o complemento do VSTO não contiver nenhuma `null` personalização do Ribbon, retorne dentro do método.

 O exemplo a seguir retorna um objeto Ribbon com base no valor de um campo.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>Executar operações caras em um segmento de execução separado
 Considere executar tarefas demoradas (como tarefas de longa duração, conexões de banco de dados ou outros tipos de chamadas de rede) em um segmento separado. Para obter mais informações, consulte [o suporte ao Threading no Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Todo o código que chama para o modelo de objeto Office deve ser executado no segmento principal.

## <a name="see-also"></a>Confira também

- [Complementos VSTO de carregamento de demanda](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Atraso no carregamento do CLR em Complementos de Escritório](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Criar suplementos do VSTO para o Office usando o Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
