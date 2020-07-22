# admin_django
@csrf_exempt
def editorImage(request):
    
    file = request.FILES['file']
    success = False
    if request.user.is_authenticated:
        try:
            image = ImageEditor(image=file)
            image.save()
            
            print(image)
            success = True
        except Exception as e:
            print(e)


    print("succes : ", success)
    data={
        'location':image.image.url,
    }
    
    return JsonResponse(data, safe=False)
