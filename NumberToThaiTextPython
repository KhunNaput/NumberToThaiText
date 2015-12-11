class ChangeNumberToText:

    def NumberToThaiText(num):
        num1 = num
        #โปรแกรมทำงานได้ถึงแค่หลักล้านล้านเท่านัน, การรับข้อมูลจะต้องเป็นข้อมูลขนิด Float หรือ Demical เท่านั้น
        txtNum = ["", "หนึ่ง", "สอง", "สาม", "สี่", "ห้า", "หก", "เจ็ด", "แปด", "เก้า"]
        last_sec_txtNum = ["", "", "ยี่", "สาม", "สี่", "ห้า", "หก", "เจ็ด", "แปด", "เก้า"]
        last_txtNum = ["", "เอ็ด", "สอง", "สาม", "สี่", "ห้า", "หก", "เจ็ด", "แปด", "เก้า"]
        txtWeight = ["","สิบ", "ร้อย", "พัน", "หมื่น", "แสน", "ล้าน", "สิบ", "ร้อย", "พัน", "หมื่น", "แสน", "ล้าน"]
        zero = "ศูนย์"

        wight = str(num1).split('.') #แยกระหว่างตัวเลขและทศนิยมออกเป็นสองส่วน

        try:
            for i in range(0, len(wight)):
                for j in wight[i]:
                   try:
                       int(j)
                   except:
                       return  "Only use 1000 or 1000.00"
        except:
           return  "Only use 1000 or 1000.00"

        #-----ส่วนของตัวเลข----------------------------------------
        type_bath = [] #เก็บข้อมูลตามหลัก
        i = 0 #ตัวแปรที่ระบุต่ำแหน่งของ Tuple
        #ตรวจสอบหลักของตัวเลขแล้วกำหนดค่าให้ จากตำแหน่งที่มากที่สุด
        for j in range(len(wight[0]) -1, -1, -1):
            if int(wight[0][i]) == 0:
                if i == (len(wight[0])-1) - 6:
                    type_bath.append(txtWeight[j])
                else:
                    type_bath.append("") #หากตัวเลขมีค่า = 0 ไม่ต้องแสดงหลัก เช่น 1000 = "หนึ่งพัน", 1100 = "หนึ่งพันหนึ่งร้อย"
            else:
                type_bath.append(txtWeight[j])
            i += 1

        val = "" #ประกาศตัวแปลเพื่อใช้ในการเก็บข้อความที่แปลง
        #ส่วนของการแปลงตัวเลข
        for i in range(0, len(wight[0])):
            if i == len(wight[0])-1:
                if int(wight[0][i-1]) == 0:
                    val += txtNum[int(wight[0][i])] + type_bath[i]
                else:
                    if len(wight[0]) == 1:
                        val += txtNum[int(wight[0][i])] + type_bath[i]
                    else:
                        val += last_txtNum[int(wight[0][i])] + type_bath[i]
            elif i == len(wight[0])-2:
                val += last_sec_txtNum[int(wight[0][i])] + type_bath[i]

            elif i == (len(wight[0])-1) - 6:
                if int(wight[0][i-1]) == 0:
                    val += txtNum[int(wight[0][i])] + type_bath[i]
                else:
                    if len(wight[0]) == 1:
                        val += txtNum[int(wight[0][i])] + type_bath[i]
                    else:
                        val += last_txtNum[int(wight[0][i])] + type_bath[i]
            elif i == (len(wight[0])-1) - 7:
                val += last_sec_txtNum[int(wight[0][i])] + type_bath[i]
            else:
                val += txtNum[int(wight[0][i])] + type_bath[i]

        if val == "":
            val += zero + "บาท"
        else:
            val += "บาท"
        #-----------------------------------------------------------------------------------------------

        #-----ส่วนของทศนิยม----------------------------------------
        try:
            wight[1]
        except:
            return val

        d = 0
        #เช็คค่าทศนิยมว่าเป็นศุนย์ทั้งหมดหรือไม่
        for i in wight[1]:
            if int(i) != 0:
                d += 1
        if d != 0:
            val += "" #ถ้าไม่เป็นศูนย์หมดก็เพื่มข้อมูล
            #เพื่อความถูกต้องของการอ่าน ทศนิยมหลักเดียวจะต้องถูกทำให้เป็น 2 หลัก
            v = []  #เก็บข้อมูลไว้ใน v[]
            if len(wight[1]) == 1:
                for i in "%s0" %(wight[1][0]):
                    v.append(i)
            else:
                for i in wight[1][:2]:
                    v.append(i)
            #เก็บหลักของสตางค์
            type_satang = []
            i = 0
            #ลักษณะการทำงานคล้าย type_bath
            for j in range(len(v) -1, -1, -1):
                if v[i] == "0":
                    type_satang.append("")
                else:
                    type_satang.append(txtWeight[j])
                i += 1
            #แปลงข้อมูลเป็นสตางค์
            for i in range(0, len(v)):
                if i == 0:
                    val += last_sec_txtNum[int(v[i])] + type_satang[i]
                else:
                    val += last_txtNum[int(v[i])] + type_satang[i]
            val += "สตางค์"
        #-----------------------------------------------------------------------------------------------
        #ส่งค่ากลับไปแสดง
        return val

