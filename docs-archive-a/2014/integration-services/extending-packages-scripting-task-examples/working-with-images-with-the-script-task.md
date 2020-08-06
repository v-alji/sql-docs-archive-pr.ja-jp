---
title: スクリプト タスクによる画像の操作 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- graphics [Integration Services]
- Script task [Integration Services], images
- Drawing namespace
- images [Integration Services]
- SSIS Script task, images
- Script task [Integration Services], examples
- thumbnails [Integration Services]
- System.Drawing namespace
- JPEG format [Integration Services]
- .jpeg files
ms.assetid: 74aeb7ab-51b2-4b9f-84ee-0b46a7908ab9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75a5b72f87a4463d7270dc9f28529a81525860cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641168"
---
# <a name="working-with-images-with-the-script-task"></a><span data-ttu-id="c8993-102">スクリプト タスクによる画像の操作</span><span class="sxs-lookup"><span data-stu-id="c8993-102">Working with Images with the Script Task</span></span>
  <span data-ttu-id="c8993-103">製品またはユーザーのデータベースには、テキストや数値データに加え、画像も頻繁に含まれています。</span><span class="sxs-lookup"><span data-stu-id="c8993-103">A database of products or users frequently includes images in addition to text and numeric data.</span></span> <span data-ttu-id="c8993-104">Microsoft .NET Framework の `System.Drawing` 名前空間では、画像を操作するためのクラスが提供されています。</span><span class="sxs-lookup"><span data-stu-id="c8993-104">The `System.Drawing` namespace in the Microsoft .NET Framework provides classes for manipulating images.</span></span>  
  
 [<span data-ttu-id="c8993-105">例 1 : 画像を JPEG 形式に変換する</span><span class="sxs-lookup"><span data-stu-id="c8993-105">Example 1: Convert Images to JPEG Format</span></span>](#example1)  
  
 [<span data-ttu-id="c8993-106">例 2 : サムネイル画像を作成および保存する</span><span class="sxs-lookup"><span data-stu-id="c8993-106">Example 2: Create and Save Thumbnail Images</span></span>](#example2)  
  
> [!NOTE]  
>  <span data-ttu-id="c8993-107">複数のパッケージでより簡単に再利用できるタスクを作成する場合は、このスクリプト タスク サンプルのコードを基にした、カスタム タスクの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="c8993-107">If you want to create a task that you can more easily reuse across multiple packages, consider using the code in this Script task sample as the starting point for a custom task.</span></span> <span data-ttu-id="c8993-108">詳細については、「 [カスタム タスクの開発](../extending-packages-custom-objects/task/developing-a-custom-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8993-108">For more information, see [Developing a Custom Task](../extending-packages-custom-objects/task/developing-a-custom-task.md).</span></span>  
  
##  <a name="example-1-description-convert-images-to-jpeg-format"></a><a name="example1"></a> <span data-ttu-id="c8993-109">例 1 の説明 : 画像を JPEG 形式に変換する</span><span class="sxs-lookup"><span data-stu-id="c8993-109">Example 1 Description: Convert Images to JPEG Format</span></span>  
 <span data-ttu-id="c8993-110">次の例では、変数で指定された画像ファイルを開き、エンコーダーを使用して圧縮 JPEG ファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="c8993-110">The following example opens an image file specified by a variable and saves it as a compressed JPEG file by using an encoder.</span></span> <span data-ttu-id="c8993-111">エンコーダー情報を取得するコードは、private 関数にカプセル化されています。</span><span class="sxs-lookup"><span data-stu-id="c8993-111">The code to retrieve encoder information is encapsulated in a private function.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="c8993-112">このスクリプト タスクの例を単一の画像ファイルで使用するように構成するには</span><span class="sxs-lookup"><span data-stu-id="c8993-112">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="c8993-113">`CurrentImageFile` という名前の文字列変数を作成し、その値を既存の画像ファイルのパスおよびファイル名に設定します。</span><span class="sxs-lookup"><span data-stu-id="c8993-113">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="c8993-114">[**スクリプトタスクエディター**] の [**スクリプト**] ページで、 `CurrentImageFile` プロパティに変数を追加し `ReadOnlyVariables` ます。</span><span class="sxs-lookup"><span data-stu-id="c8993-114">On the **Script** page of the **Script Task Editor**, add the `CurrentImageFile` variable to the `ReadOnlyVariables` property.</span></span>  
  
3.  <span data-ttu-id="c8993-115">このスクリプト プロジェクトでは、参照を `System.Drawing` 名前空間に設定します。</span><span class="sxs-lookup"><span data-stu-id="c8993-115">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
4.  <span data-ttu-id="c8993-116">実際のコードでは、`Imports` ステートメントを使用して、`System.Drawing` および `System.IO` 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="c8993-116">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="c8993-117">このスクリプト タスクの例を複数の画像ファイルで使用するように構成するには</span><span class="sxs-lookup"><span data-stu-id="c8993-117">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="c8993-118">Foreach ループ コンテナー内にスクリプト タスクを入れます。</span><span class="sxs-lookup"><span data-stu-id="c8993-118">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="c8993-119">**[Foreach ループ エディター]** の **[コレクション]** ページで、列挙子として **[Foreach File 列挙子]** を選択し、次に、ソース ファイルのパスおよびファイル マスク ("\*.bmp" など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8993-119">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the enumerator, and specify the path and file mask of the source files, such as "\*.bmp."</span></span>  
  
3.  <span data-ttu-id="c8993-120">**[変数のマッピング]** ページで、`CurrentImageFile` 変数をインデックス 0 にマップします。</span><span class="sxs-lookup"><span data-stu-id="c8993-120">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="c8993-121">この変数は、列挙子が繰り返されるたびに、現在のファイル名をスクリプト タスクに渡します。</span><span class="sxs-lookup"><span data-stu-id="c8993-121">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8993-122">この手順は、単一の画像ファイルで使用する場合の手順としてリストされているものに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c8993-122">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-1-code"></a><span data-ttu-id="c8993-123">例 1 のコード</span><span class="sxs-lookup"><span data-stu-id="c8993-123">Example 1 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    'Create and initialize variables.  
    Dim currentFile As String  
    Dim newFile As String  
    Dim bmp As Bitmap  
    Dim eps As New Imaging.EncoderParameters(1)  
    Dim ici As Imaging.ImageCodecInfo  
    Dim supportedExtensions() As String = _  
        {".BMP", ".GIF", ".JPG", ".JPEG", ".EXIF", ".PNG", _  
        ".TIFF", ".TIF", ".ICO", ".ICON"}  
  
    Try  
        'Store the variable in a string for local manipulation.  
        currentFile = Dts.Variables("CurrentImageFile").Value.ToString  
        'Check the extension of the file against a list of  
        'files that the Bitmap class supports.  
        If Array.IndexOf(supportedExtensions, _  
            Path.GetExtension(currentFile).ToUpper) > -1 Then  
  
            'Load the file.  
            bmp = New Bitmap(currentFile)  
  
            'Calculate the new name for the compressed image.  
            'Note: This will overwrite existing JPEGs.  
            newFile = Path.Combine( _  
                Path.GetDirectoryName(currentFile), _  
                String.Concat(Path.GetFileNameWithoutExtension(currentFile), _  
                ".jpg"))  
  
            'Specify the compression ratio (0=worst quality, 100=best quality).  
            eps.Param(0) = New Imaging.EncoderParameter( _  
                Imaging.Encoder.Quality, 75)  
  
            'Retrieve the ImageCodecInfo associated with the jpeg format.  
            ici = GetEncoderInfo("image/jpeg")  
  
            'Save the file, compressing it into the jpeg encoding.  
            bmp.Save(newFile, ici, eps)  
        Else  
            'The file is not supported by the Bitmap class.  
            Dts.Events.FireWarning(0, "Image Resampling Sample", _  
                "File " & currentFile & " is not a supported format.", _  
                "", 0)  
         End If  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        'An error occurred.  
        Dts.Events.FireError(0, "Image Resampling Sample", _  
            ex.Message & ControlChars.CrLf & ex.StackTrace, _  
            String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Function GetEncoderInfo(ByVal mimeType As String) As Imaging.ImageCodecInfo  
  
    'The available image codecs are returned as an array,  
    'which requires code to iterate until the specified codec is found.  
  
    Dim count As Integer  
    Dim encoders() As Imaging.ImageCodecInfo  
  
    encoders = Imaging.ImageCodecInfo.GetImageEncoders()  
  
    For count = 0 To encoders.Length  
        If encoders(count).MimeType = mimeType Then  
            Return encoders(count)  
        End If  
    Next  
  
    'This point is only reached if a codec is not found.  
    Err.Raise(513, "Image Resampling Sample", String.Format( _  
        "The {0} codec is not available. Unable to compress file.", _  
            mimeType))  
    Return Nothing  
  
End Function  
  
```  
  
##  <a name="example-2-description-create-and-save-thumbnail-images"></a><a name="example2"></a> <span data-ttu-id="c8993-124">例 2 の説明 : サムネイル画像を作成および保存する</span><span class="sxs-lookup"><span data-stu-id="c8993-124">Example 2 Description: Create and Save Thumbnail Images</span></span>  
 <span data-ttu-id="c8993-125">次の例では、変数で指定された画像ファイルを開いて、一定の縦横比を維持しながら画像のサムネイルを作成し、ファイル名を変更してサムネイルを保存します。</span><span class="sxs-lookup"><span data-stu-id="c8993-125">The following example opens an image file specified by a variable, creates a thumbnail of the image while maintaining a constant aspect ratio, and saves the thumbnail with a modified file name.</span></span> <span data-ttu-id="c8993-126">一定の縦横比を維持しながらサムネイルの高さと幅を計算するコードは、private サブルーチンでカプセル化されています。</span><span class="sxs-lookup"><span data-stu-id="c8993-126">The code that calculates the height and width of the thumbnail while maintaining a constant aspect ratio is encapsulated in a private subroutine.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-a-single-image-file"></a><span data-ttu-id="c8993-127">このスクリプト タスクの例を単一の画像ファイルで使用するように構成するには</span><span class="sxs-lookup"><span data-stu-id="c8993-127">To configure this Script Task example for use with a single image file</span></span>  
  
1.  <span data-ttu-id="c8993-128">`CurrentImageFile` という名前の文字列変数を作成し、その値を既存の画像ファイルのパスおよびファイル名に設定します。</span><span class="sxs-lookup"><span data-stu-id="c8993-128">Create a string variable named `CurrentImageFile` and set its value to the path and file name of an existing image file.</span></span>  
  
2.  <span data-ttu-id="c8993-129">次に `MaxThumbSize` 整数変数を作成し、100 などのピクセル値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c8993-129">Also create the `MaxThumbSize` integer variable and assign a value in pixels, such as 100.</span></span>  
  
3.  <span data-ttu-id="c8993-130">[**スクリプトタスクエディター**] の [**スクリプト**] ページで、両方の変数をプロパティに追加し `ReadOnlyVariables` ます。</span><span class="sxs-lookup"><span data-stu-id="c8993-130">On the **Script** page of the **Script Task Editor**, add both variables to the `ReadOnlyVariables` property.</span></span>  
  
4.  <span data-ttu-id="c8993-131">このスクリプト プロジェクトでは、参照を `System.Drawing` 名前空間に設定します。</span><span class="sxs-lookup"><span data-stu-id="c8993-131">In the script project, set a reference to the `System.Drawing` namespace.</span></span>  
  
5.  <span data-ttu-id="c8993-132">実際のコードでは、`Imports` ステートメントを使用して、`System.Drawing` および `System.IO` 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="c8993-132">In your code, use `Imports` statements to import the `System.Drawing` and `System.IO` namespaces.</span></span>  
  
#### <a name="to-configure-this-script-task-example-for-use-with-multiple-image-files"></a><span data-ttu-id="c8993-133">このスクリプト タスクの例を複数の画像ファイルで使用するように構成するには</span><span class="sxs-lookup"><span data-stu-id="c8993-133">To configure this Script Task example for use with multiple image files</span></span>  
  
1.  <span data-ttu-id="c8993-134">Foreach ループ コンテナー内にスクリプト タスクを入れます。</span><span class="sxs-lookup"><span data-stu-id="c8993-134">Place the Script task within a Foreach Loop container.</span></span>  
  
2.  <span data-ttu-id="c8993-135">**[Foreach ループ エディター]** の **[コレクション]** ページで、**[列挙子]** として **[Foreach File 列挙子]** を選択し、次に、ソース ファイルのパスおよびファイル マスク ("\*.jpg" など) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8993-135">On the **Collection** page of the **Foreach Loop Editor**, select the **Foreach File Enumerator** as the **Enumerator**, and specify the path and file mask of the source files, such as "\*.jpg."</span></span>  
  
3.  <span data-ttu-id="c8993-136">**[変数のマッピング]** ページで、`CurrentImageFile` 変数をインデックス 0 にマップします。</span><span class="sxs-lookup"><span data-stu-id="c8993-136">On the **Variable Mappings** page, map the `CurrentImageFile` variable to Index 0.</span></span> <span data-ttu-id="c8993-137">この変数は、列挙子が繰り返されるたびに、現在のファイル名をスクリプト タスクに渡します。</span><span class="sxs-lookup"><span data-stu-id="c8993-137">This variable passes the current file name to the Script task on each iteration of the enumerator.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="c8993-138">この手順は、単一の画像ファイルで使用する場合の手順としてリストされているものに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c8993-138">These steps are in addition to the steps listed in the procedure for use with a single image file.</span></span>  
  
### <a name="example-2-code"></a><span data-ttu-id="c8993-139">例 2 のコード</span><span class="sxs-lookup"><span data-stu-id="c8993-139">Example 2 Code</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim currentImageFile As String  
    Dim currentImage As Image  
    Dim maxThumbSize As Integer  
    Dim thumbnailImage As Image  
    Dim thumbnailFile As String  
    Dim thumbnailHeight As Integer  
    Dim thumbnailWidth As Integer  
  
    currentImageFile = Dts.Variables("CurrentImageFile").Value.ToString  
    thumbnailFile = Path.Combine( _  
        Path.GetDirectoryName(currentImageFile), _  
        String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), _  
        "_thumbnail.jpg"))  
  
    Try  
        currentImage = Image.FromFile(currentImageFile)  
  
        maxThumbSize = CType(Dts.Variables("MaxThumbSize").Value, Integer)  
        CalculateThumbnailSize( _  
            maxThumbSize, currentImage, thumbnailWidth, thumbnailHeight)  
  
        thumbnailImage = currentImage.GetThumbnailImage( _  
           thumbnailWidth, thumbnailHeight, Nothing, Nothing)  
        thumbnailImage.Save(thumbnailFile)  
        Dts.TaskResult = ScriptResults.Success  
    Catch ex As Exception  
        Dts.Events.FireError(0, "Script Task Example", _  
        ex.Message & ControlChars.CrLf & ex.StackTrace, _  
        String.Empty, 0)  
        Dts.TaskResult = ScriptResults.Failure  
    End Try  
  
End Sub  
  
Private Sub CalculateThumbnailSize( _  
    ByVal maxSize As Integer, ByVal sourceImage As Image, _  
    ByRef thumbWidth As Integer, ByRef thumbHeight As Integer)  
  
    If sourceImage.Width > sourceImage.Height Then  
        thumbWidth = maxSize  
        thumbHeight = CInt((maxSize / sourceImage.Width) * sourceImage.Height)  
    Else  
        thumbHeight = maxSize  
        thumbWidth = CInt((maxSize / sourceImage.Height) * sourceImage.Width)  
    End If  
  
End Sub  
```  
  
```csharp  
bool ThumbnailCallback()  
        {  
            return false;  
        }  
        public void Main()  
        {  
  
            string currentImageFile;  
            Image currentImage;  
            int maxThumbSize;  
            Image thumbnailImage;  
            string thumbnailFile;  
            int thumbnailHeight = 0;  
            int thumbnailWidth = 0;  
  
            currentImageFile = Dts.Variables["CurrentImageFile"].Value.ToString();  
            thumbnailFile = Path.Combine(Path.GetDirectoryName(currentImageFile), String.Concat(Path.GetFileNameWithoutExtension(currentImageFile), "_thumbnail.jpg"));  
  
            try  
            {  
  
                currentImage = Image.FromFile(currentImageFile);  
  
                maxThumbSize = (int)Dts.Variables["MaxThumbSize"].Value;  
                CalculateThumbnailSize(maxThumbSize, currentImage, ref thumbnailWidth, ref thumbnailHeight);  
  
                Image.GetThumbnailImageAbort myCallback = new Image.GetThumbnailImageAbort(ThumbnailCallback);  
  
                thumbnailImage = currentImage.GetThumbnailImage(thumbnailWidth, thumbnailHeight, ThumbnailCallback, IntPtr.Zero);  
                thumbnailImage.Save(thumbnailFile);  
                Dts.TaskResult = (int)ScriptResults.Success;  
            }  
            catch (Exception ex)  
            {  
                Dts.Events.FireError(0, "Script Task Example", ex.Message + "\r" + ex.StackTrace, String.Empty, 0);  
                Dts.TaskResult = (int)ScriptResults.Failure;  
            }  
  
        }  
  
        private void CalculateThumbnailSize(int maxSize, Image sourceImage, ref int thumbWidth, ref int thumbHeight)  
        {  
  
            if (sourceImage.Width > sourceImage.Height)  
            {  
                thumbWidth = maxSize;  
                thumbHeight = (int)(sourceImage.Height * maxSize / sourceImage.Width);  
            }  
            else  
            {  
                thumbHeight = maxSize;  
                thumbWidth = (int)(sourceImage.Width * maxSize / sourceImage.Height);  
  
            }  
  
        }  
  
```  
  
<span data-ttu-id="c8993-140">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="c8993-140">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="c8993-141">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8993-141">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="c8993-142">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="c8993-142">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="c8993-143">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="c8993-143">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
