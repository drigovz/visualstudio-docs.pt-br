---
title: Combine personalizações do VBA e no nível do documento
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b3bab9c132439c6efa53842f1e13c6c5be31db00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70977596"
---
# <a name="combine-vba-and-document-level-customizations"></a>Combine personalizações do VBA e no nível do documento
  Você pode usar o código Visual Basic for Applications (VBA) em um documento que faz parte de uma personalização em nível de documento para Microsoft Office Word ou Microsoft Office Excel. Você pode chamar o código VBA no documento a partir do assembly de personalização ou pode configurar seu projeto para habilitar o código VBA no documento para chamar o código no assembly de personalização.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>Comportamento do código VBA em uma personalização no nível do documento
 Quando você abre o projeto no Visual Studio, o documento é aberto no modo de design. O código VBA não é executado quando o documento está no modo de design, para que você possa trabalhar no documento e no código sem executar o código VBA.

 Quando você executa a solução, os manipuladores de eventos no VBA e no assembly de personalização coletam eventos que são gerados no documento e ambos os conjuntos de código são executados. Você não pode determinar com antecedência qual código será executado antes do outro; Você deve determinar isso por meio de testes em cada caso individual. Você poderá obter resultados inesperados se os dois conjuntos de código não forem cuidadosamente coordenados e testados.

## <a name="call-vba-code-from-the-customization-assembly"></a>Chamar código VBA do assembly de personalização
 Você pode chamar macros em documentos do Word e pode chamar macros e funções em pastas de trabalho do Excel. Para tal, use um dos seguintes métodos:

- Para o Word, chame o <xref:Microsoft.Office.Interop.Word._Application.Run%2A> método da <xref:Microsoft.Office.Interop.Word.Application> classe.

- Para o Excel, chame o <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> método da <xref:Microsoft.Office.Interop.Excel.Application> classe.

  Para cada método, o primeiro parâmetro identifica o nome da macro ou função que você deseja chamar, e os parâmetros opcionais restantes especificam os parâmetros a serem passados para a macro ou função. O primeiro parâmetro pode ter formatos diferentes para o Word e o Excel:

- Para o Word, o primeiro parâmetro é uma cadeia de caracteres que pode ser qualquer combinação de modelo, módulo e nome de macro. Se você especificar o nome do documento, seu código só poderá executar macros em documentos relacionados ao contexto atual — não apenas qualquer macro em nenhum documento.

- Para o Excel, o primeiro parâmetro pode ser uma cadeia de caracteres que especifica o nome da macro, um <xref:Microsoft.Office.Interop.Excel.Range> que indica onde a função é, ou uma ID de registro para uma função de dll registrada (XLL). Se você passar uma cadeia de caracteres, a cadeia de caracteres será avaliada no contexto da planilha ativa.

  O exemplo de código a seguir mostra como chamar uma macro chamada `MyMacro` de um projeto de nível de documento para o Excel. Este exemplo pressupõe que `MyMacro` é definido em `Sheet1` .

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Para obter informações sobre como usar a `missing` variável global no lugar de parâmetros opcionais no Visual C#, consulte [escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md).

## <a name="call-code-in-document-level-customizations-from-vba"></a>Código de chamada em personalizações em nível de documento do VBA
 Você pode configurar um projeto de nível de documento para o Word ou o Excel de forma que o código Visual Basic for Applications (VBA) no documento possa chamar o código no assembly de personalização. Isso é útil nos seguintes cenários:

- Você deseja estender o código VBA existente em um documento usando recursos em uma personalização em nível de documento associada ao mesmo documento.

- Você deseja tornar os serviços desenvolvidas em uma personalização em nível de documento disponíveis para os usuários finais que podem acessar os serviços escrevendo código VBA no documento.

  As ferramentas de desenvolvimento do Office no Visual Studio fornecem um recurso semelhante para os suplementos do VSTO. Se você estiver desenvolvendo um suplemento do VSTO, poderá chamar o código em seu suplemento do VSTO de outras soluções de Microsoft Office. Para obter mais informações, consulte [chamar código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

> [!NOTE]
> Este recurso não pode ser usado em projetos de modelo do Word. Ele pode ser usado somente no documento do Word, na pasta de trabalho do Excel ou em projetos de modelo do Excel.

## <a name="requirements"></a>Requisitos
 Antes que você possa habilitar o código VBA para chamar o assembly de personalização, seu projeto deve atender aos seguintes requisitos:

- O documento deve ter uma das seguintes extensões de nome de arquivo:

  - Para Word: *. docm* ou *. doc*

  - Para Excel: *. xlsm*, *. xltm*, *. xls*ou *. xlt*

- O documento já deve conter um projeto do VBA que tenha código VBA.

- O código VBA no documento deve ter permissão para ser executado sem solicitar que o usuário habilite macros. Você pode confiar no código VBA para executar adicionando o local do projeto do Office à lista de locais confiáveis nas configurações da central de confiabilidade do Word ou Excel.

- O projeto do Office deve conter pelo menos uma classe pública que contenha um ou mais membros públicos que você está expondo ao VBA.

     Você pode expor métodos, propriedades e eventos para o VBA. A classe que você expõe pode ser uma classe de item de host (por exemplo `ThisDocument` , para Word ou `ThisWorkbook` e `Sheet1` para Excel) ou outra classe que você define em seu projeto. Para obter mais informações sobre itens de host, consulte [visão geral de itens de host e controles de host](../vsto/host-items-and-host-controls-overview.md).

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>Habilitar o código VBA para chamar o assembly de personalização
 Há duas maneiras diferentes de expor membros em um assembly de personalização para código VBA no documento:

- Você pode expor membros de uma classe de item de host em um [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projeto do para o VBA. Para fazer isso, defina a propriedade **EnableVbaCallers** do item de host como **true** na janela **Propriedades** enquanto o item de host (ou seja, o documento, a planilha ou a pasta de trabalho) estiver aberto no designer. O Visual Studio executa automaticamente todo o trabalho necessário para permitir que o código VBA chame os membros da classe.

- Você pode expor membros em qualquer classe pública em um projeto do Visual C#, ou membros em uma classe de item que não seja de host em um [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projeto, para o VBA. Essa opção fornece mais liberdade para escolher quais classes você expõe para o VBA, mas também requer mais etapas manuais.

   Para fazer isso, você deve executar as seguintes etapas principais:

  1. Expor a classe para COM.

  2. Substitua o método **GetAutomationObject** de uma classe de item de host em seu projeto para retornar uma instância da classe que você está expondo ao VBA.

  3. Defina a propriedade **ReferenceAssemblyFromVbaProject** de qualquer classe de item de host no projeto como **true**. Isso incorpora a biblioteca de tipos do assembly de personalização ao assembly e adiciona uma referência à biblioteca de tipos ao projeto do VBA no documento.

  Para obter instruções detalhadas, consulte [como: expor código ao VBA em um projeto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) e [como: expor código ao VBA em um projeto do Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md).

  As propriedades **EnableVbaCallers** e **ReferenceAssemblyFromVbaProject** estão disponíveis apenas na janela **Propriedades** em tempo de design; Eles não podem ser usados em tempo de execução. Para exibir as propriedades, abra o designer de um item de host no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Para obter mais informações sobre as tarefas específicas que o Visual Studio executa ao definir essas propriedades, consulte [tarefas executadas pelas propriedades do item de host](#PropertyTasks).

> [!NOTE]
> Se a pasta de trabalho ou o documento ainda não contiver código VBA ou se o código VBA no documento não for confiável para execução, você receberá uma mensagem de erro ao definir a propriedade **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** como **true**. Isso ocorre porque o Visual Studio não pode modificar o projeto do VBA no documento nessa situação.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>Usar membros no código VBA para chamar o assembly de personalização
 Depois de configurar seu projeto para habilitar o código VBA para chamar o assembly de personalização, o Visual Studio adiciona os seguintes membros ao projeto do VBA no documento:

- Para todos os projetos, o Visual Studio adiciona um método global chamado `GetManagedClass` .

- Para [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] projetos nos quais você expõe membros de uma classe de item de host usando a propriedade **EnableVbaCallers** , o Visual Studio também adiciona uma propriedade chamada `CallVSTOAssembly` ao `ThisDocument` módulo,, `ThisWorkbook` `Sheet1` , `Sheet2` ou `Sheet3` no projeto do VBA.

  Você pode usar a `CallVSTOAssembly` propriedade ou o `GetManagedClass` método para acessar membros públicos da classe que você expôs ao código VBA no projeto.

> [!NOTE]
> Embora você desenvolva e implante sua solução, há várias cópias diferentes do documento em que você pode adicionar o código VBA. Para obter mais informações, consulte [diretrizes para adicionar código VBA ao documento](#Guidelines).

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Usar a propriedade CallVSTOAssembly em um projeto Visual Basic
 Use a `CallVSTOAssembly` propriedade para acessar membros públicos que você adicionou à classe de item de host. Por exemplo, a macro VBA a seguir chama um método chamado `MyVSTOMethod` que é definido na `Sheet1` classe em um projeto de pasta de trabalho do Excel.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 Essa propriedade é uma maneira mais conveniente de chamar o assembly de personalização do que usar o `GetManagedClass` método diretamente. `CallVSTOAssembly` Retorna um objeto que representa a classe de item de host que você expôs ao VBA. Os membros e os parâmetros de método do objeto retornado aparecem no IntelliSense.

 A `CallVSTOAssembly` propriedade tem uma declaração semelhante ao código a seguir. Esse código pressupõe que você tenha exposto a `Sheet1` classe de item de host em um projeto de pasta de trabalho do Excel chamado `ExcelWorkbook1` para VBA.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>Usar o método GetManagedClass
 Para usar o `GetManagedClass` método global, passe o objeto VBA que corresponde à classe de item de host que contém a substituição do método **GetAutomationObject** . Em seguida, use o objeto retornado para acessar a classe que você expôs ao VBA.

 Por exemplo, a macro VBA a seguir chama um método chamado `MyVSTOMethod` que é definido na `Sheet1` classe de item de host em um projeto de pasta de trabalho do Excel chamado `ExcelWorkbook1` .

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 O `GetManagedClass` método tem a declaração a seguir.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 Esse método retorna um objeto que representa a classe que você expôs ao VBA. Os membros e os parâmetros de método do objeto retornado aparecem no IntelliSense.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> Diretrizes para adicionar código VBA ao documento
 Há várias cópias diferentes do documento em que você pode adicionar código VBA que chama a personalização no nível do documento.

 Ao desenvolver e testar sua solução, você pode escrever código VBA no documento que é aberto enquanto depura ou executa o projeto no Visual Studio (ou seja, o documento na pasta de saída de compilação). No entanto, qualquer código VBA que você adicionar a este documento será substituído na próxima vez que você compilar o projeto, pois o Visual Studio substitui o documento na pasta de saída da compilação por uma cópia do documento da pasta principal do projeto.

 Se você quiser salvar o código VBA que você adicionar ao documento durante a depuração ou a execução da solução, copie o código do VBA para o documento na pasta do projeto. Para obter mais informações sobre o processo de compilação, consulte [criar soluções do Office](../vsto/building-office-solutions.md).

 Quando você estiver pronto para implantar sua solução, há três locais de documentos principais nos quais você pode adicionar o código VBA.

### <a name="in-the-project-folder-on-the-development-computer"></a>Na pasta do projeto no computador de desenvolvimento
 Esse local é conveniente se você tiver controle total sobre o código VBA no documento e o código de personalização. Como o documento está no computador de desenvolvimento, você pode facilmente modificar o código do VBA se alterar o código de personalização. O código do VBA que você adiciona a essa cópia do documento permanece no documento quando você cria, depura e publica sua solução.

 Você não pode adicionar o código VBA ao documento enquanto ele está aberto no designer. Você deve primeiro fechar o documento no designer e, em seguida, abrir o documento diretamente no Word ou no Excel.

> [!CAUTION]
> Se você adicionar código VBA que é executado quando o documento é aberto, em casos raros, esse código pode corromper o documento ou impedir que ele seja aberto no designer.

### <a name="in-the-publish-or-installation-folder"></a>Na pasta publicar ou instalar
 Em alguns casos, pode ser adequado adicionar o código VBA ao documento na pasta de publicação ou instalação. Por exemplo, você pode escolher essa opção se o código do VBA for escrito e testado por um desenvolvedor diferente em um computador que não tenha o Visual Studio instalado.

 Se os usuários instalarem a solução diretamente da pasta de publicação, você deverá adicionar o código VBA ao documento toda vez que publicar a solução. O Visual Studio substitui o documento no local de publicação quando você publica a solução.

 Se os usuários instalarem a solução de uma pasta de instalação diferente da pasta de publicação, você poderá evitar adicionar o código VBA no documento sempre que publicar a solução. Quando uma atualização de publicação estiver pronta para ser movida da pasta de publicação para a pasta de instalação, copie todos os arquivos para a pasta de instalação, exceto para o documento.

### <a name="on-the-end-user-computer"></a>No computador do usuário final
 Se os usuários finais forem desenvolvedores do VBA que estão chamando serviços que você fornece na personalização no nível do documento, você poderá dizer a eles como chamar seu código usando a `CallVSTOAssembly` propriedade ou o `GetManagedClass` método em suas cópias do documento. Quando você publica atualizações na solução, o código do VBA no documento no computador do usuário final não será substituído, pois o documento não será modificado por atualizações de publicação.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> Tarefas executadas pelas propriedades do item de host
 Quando você usa as propriedades **EnableVbaCallers** e **ReferenceAssemblyFromVbaProject** , o Visual Studio executa diferentes conjuntos de tarefas.

### <a name="enablevbacallers"></a>EnableVbaCallers
 Quando você define a propriedade **EnableVbaCallers** de um item de host como **true** em um projeto Visual Basic, o Visual Studio executa as seguintes tarefas:

1. Ele adiciona os <xref:Microsoft.VisualBasic.ComClassAttribute> <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributos e à classe de item de host.

2. Ele substitui o método **GetAutomationObject** da classe de item de host.

3. Ele define a propriedade **ReferenceAssemblyFromVbaProject** do item de host como **true**.

   Quando você define a propriedade **EnableVbaCallers** de volta como **false**, o Visual Studio executa as seguintes tarefas:

4. Ele remove os <xref:Microsoft.VisualBasic.ComClassAttribute> <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributos e da `ThisDocument` classe.

5. Ele remove o método **GetAutomationObject** da classe de item de host.

   > [!NOTE]
   > O Visual Studio não define automaticamente a propriedade **ReferenceAssemblyFromVbaProject** de volta como **false**. Você pode definir essa propriedade como **false** manualmente usando a janela **Propriedades** .

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Quando a propriedade **ReferenceAssemblyFromVbaProject** de qualquer item de host em um projeto Visual Basic ou Visual C# é definida como **true**, o Visual Studio executa as seguintes tarefas:

1. Ele gera uma biblioteca de tipos para o assembly de personalização e insere a biblioteca de tipos no assembly.

2. Ele adiciona uma referência às seguintes bibliotecas de tipos no projeto do VBA no documento:

   - A biblioteca de tipos para seu assembly de personalização.

   - As ferramentas de Microsoft Visual Studio para a biblioteca de tipos do mecanismo de execução do Office 9,0. Essa biblioteca de tipos está incluída no [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

   Quando a propriedade **ReferenceAssemblyFromVbaProject** é definida de volta como **false**, o Visual Studio executa as seguintes tarefas:

3. Ele remove as referências de biblioteca de tipos do projeto do VBA no documento.

4. Ele remove a biblioteca de tipos inserida do assembly.

## <a name="troubleshoot"></a>Solucionar problemas
 A tabela a seguir lista alguns erros comuns e sugestões para corrigir os erros.

|Erro|Sugestão|
|-----------|----------------|
|Depois de definir a propriedade **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** , uma mensagem de erro informa que o documento não contém um projeto do VBA ou você não tem permissão para acessar o projeto do VBA no documento.|Verifique se o documento no projeto contém pelo menos uma macro do VBA, se o projeto do VBA tem confiança suficiente para ser executado e se o projeto do VBA não está protegido por senha.|
|Depois de definir a propriedade **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** , uma mensagem de erro informa que a <xref:System.Runtime.InteropServices.GuidAttribute> declaração está ausente ou corrompida.|Verifique se a <xref:System.Runtime.InteropServices.GuidAttribute> declaração está localizada no arquivo *AssemblyInfo.cs* ou *AssemblyInfo. vb* em seu projeto e se esse atributo está definido como um GUID válido.|
|Depois de definir a propriedade **EnableVbaCallers** ou **ReferenceAssemblyFromVbaProject** , uma mensagem de erro informa que o número de versão especificado pelo <xref:System.Reflection.AssemblyVersionAttribute> não é válido.|Verifique se a <xref:System.Reflection.AssemblyVersionAttribute> declaração no arquivo *AssemblyInfo.cs* ou *AssemblyInfo. vb* em seu projeto está definida como um número de versão de assembly válido. Para obter informações sobre números de versão de assembly válidos, consulte a <xref:System.Reflection.AssemblyVersionAttribute> classe.|
|Depois de renomear o assembly de personalização, o código do VBA que chama o assembly de personalização para de funcionar.|Se você alterar o nome do assembly de personalização depois de expô-lo ao código do VBA, o link entre o projeto do VBA no documento e o assembly de personalização será interrompido. Para corrigir esse problema, altere a propriedade **ReferenceFromVbaAssembly** em seu projeto para **false** e, em seguida, volte para **true**e, em seguida, substitua todas as referências ao nome do assembly antigo no código do VBA pelo novo nome do assembly.|

## <a name="see-also"></a>Confira também
- [Como: expor código ao VBA em um projeto Visual Basic](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [Como: expor código ao VBA em um projeto do Visual C&#35;](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [Walkthrough: chamar o código do VBA em um projeto Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [Walkthrough: chamar o código do VBA em um projeto do Visual C&#35;](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Soluções do VBA e do Office no Visual Studio comparadas](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [Programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md)
