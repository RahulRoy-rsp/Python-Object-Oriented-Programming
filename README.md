# Python Object Oriented Programming
This repository will help you understand *Object Oriented Programming* approach in Python

---

- Lets first see the below two programs

    **Approach 1 (Non-Object Oriented)**
    ```python
    from datetime import datetime

    def getValues(input_number, sq_or_cb):
        res_val = input_number**2 if sq_or_cb == "square" else input_number**3
        res_calc_at = calculatedAt()
        
        return res_val, res_calc_at
            
    def calculatedAt():
        now = datetime.now()
        current_time = now.strftime("%H:%M:%S")
        
        return current_time


    def extractResults(input_number, sq_or_cb, result_val, result_calc_at):
        result_string = f"""
        The {sq_or_cb} value of {input_number} is {result_val} and it was calculated at {result_calc_at}.
        """
        
        return(result_string)


    if __name__ == "__main__":
        input_number = int(input("Enter a number: "))
        raised_to = int(input("Enter 2 (for square) or 3 (for cube): "))
        
        assert raised_to in [2, 3], f"Please enter 2 or 3 only. You entered {raised_to}"
        
        sq_or_cb = "square" if raised_to == 2 else "cube"
        res_val, res_calc_at = getValues(input_number, sq_or_cb)
        
        print(extractResults(input_number, sq_or_cb, res_val, res_calc_at))
    ```


    **Approach 2 (Object Oriented)**
    ```python
    from  datetime import datetime

    class RaiseTo:
        
        def __init__(self, input_number, raised_by):
            self.input_number = input_number
            self.raised_by = raised_by
            self.sq_or_cb = "square" if raised_by == 2 else "cube"
            
            self.result_val, self.result_calc_at = self.__getValues()
        
        
        def __getValues(self):
            res_val = self.input_number**2 if self.sq_or_cb == "square" else self.input_number**3
            res_calc_at = self.__calculatedAt()
            
            return res_val, res_calc_at
        
        
        def __calculatedAt(self):
            now = datetime.now()
            current_time = now.strftime("%H:%M:%S")
            
            return current_time
        
        
        def extractResults(self):
            result_string = f"""
            The {self.sq_or_cb} value of {self.input_number} is {self.result_val} and it was calculated at {self.result_calc_at}.
            """
            
            print(result_string)

    if __name__ == "__main__":
        input_number = int(input("Enter a number: "))
        raised_to = int(input("Enter 2 (for square) or 3 (for cube): "))
        
        assert raised_to in [2, 3], f"Please enter 2 or 3 only. You entered {raised_to}"
            
        object1 = RaiseTo(input_number, raised_to)
        object1.extractResults()
    ```
