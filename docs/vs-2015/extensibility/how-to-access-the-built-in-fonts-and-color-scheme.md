---
title: Como acessar as fontes internas e o esquema de cores | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685317"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Como acessar o esquema interno de cores e fontes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O IDE (ambiente de desenvolvimento integrado) do Visual Studio tem um esquema de fontes e cores associadas à janela do editor. Você pode acessar esse esquema por meio da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.  
  
 Para usar o esquema interno de fontes e cores, um VSPackage deve:  
  
- Defina uma categoria a ser usada com o serviço de fontes e cores padrão.  
  
- Registre a categoria com o servidor de fontes e cores padrão.  
  
- Avise ao IDE que uma janela específica usa os itens de exibição internos e as categorias usando as `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interfaces e `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` .  
  
  O IDE usa a categoria resultante como um identificador para a janela. O nome da categoria é exibido na caixa suspensa **Mostrar configurações de:** na página de propriedades **fontes e cores** .  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Para definir uma categoria usando fontes e cores internas  
  
1. Crie um GUID arbitrário.  
  
    Esse GUID é usado para identificar exclusivamente uma categoria<strong>.</strong> Essa categoria reutiliza a especificação de fontes e cores padrão do IDE.  
  
   > [!NOTE]
   > Ao recuperar dados de fonte e cor com o <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> ou outras interfaces, VSPackages Use esse GUID para referenciar informações internas.  
  
2. O nome da categoria deve ser adicionado a uma tabela de cadeia de caracteres dentro do arquivo de recursos (. rc) do VSPackage, para que possa ser localizado conforme necessário quando exibido no IDE.  
  
    Para obter mais informações, consulte [adicionando ou excluindo uma cadeia de caracteres](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Para registrar uma categoria usando fontes e cores internas  
  
1. Construa um tipo especial de entrada de registro de categoria no seguinte local:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* é o nome não localizado da categoria.  
  
2. Preencha o registro para usar as fontes de ações e o esquema de cores com quatro valores:  
  
    |Nome|Tipo|Dados|Descrição|  
    |----------|----------|----------|-----------------|  
    |Categoria|REG_SZ|GUID|Um GUID arbitrário que identifica uma categoria que contém a fonte de ações e o esquema de cores.|  
    |Pacote|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Esse GUID é usado por todos os VSPackages que usam as configurações de fonte e cor padrão.|  
    |NameID|REG_DWORD|ID|A ID de recurso de um nome de categoria localizável no VSPackage.|  
    |ToolWindowPackage|REG_SZ|GUID|O GUID do VSPackage que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Para iniciar o uso de fontes e cores fornecidas pelo sistema  
  
1. Crie uma instância da `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` interface como parte da implementação e da inicialização da janela.  
  
2. Chame o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> método para obter uma instância da `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` interface correspondente à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> instância atual.  
  
3. Chame <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> duas vezes.  
  
   - Chame uma vez com `VSEDITPROPID_ViewGeneral_ColorCategory` como um argumento.  
  
   - Chame uma vez com `VSEDITPROPID_ViewGeneral_FontCategory` como um argumento.  
  
     Isso define e expõe os serviços padrão de fontes e cores como uma propriedade da janela.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir inicia o uso de fontes e cores internas.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Usando fontes e cores](../extensibility/using-fonts-and-colors.md)   
 [Obtendo informações de fonte e cor para a colorização de texto](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Acessando configurações de fonte e de cor armazenadas](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Visão geral de cor e de fonte](../extensibility/font-and-color-overview.md)
