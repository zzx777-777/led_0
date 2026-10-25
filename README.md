[README.md](https://github.com/user-attachments/files/33930238/README.md)
# 电控组首次培训作业
- **姓名：张正轩**
- ***学号：20263008261***

{
uint32_t nowTick = HAL_GetTick();

if(nowTick - lastTick >= 500)

{
    lastTick = nowTick;
    
    switch(ledState)
    
    {
        case 0:
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_SET);
            
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_RESET);
            
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_RESET);
            
            ledState = 1;
            
            break;
            
        case 1:
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
            
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_SET);
            
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_RESET);
            
            ledState = 2;
            
            break;
        case 2:
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_0, GPIO_PIN_RESET);
            
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_1, GPIO_PIN_RESET);
            
            HAL_GPIO_WritePin(GPIOA, GPIO_PIN_2, GPIO_PIN_SET);
            
            ledState = 0;
            
            break;
        default:
        
            ledState = 0;
            
            break;
}
}
1. 定义变量：记录上一次LED翻转的时间点  last_time ，设置翻转间隔  LED_INTERVAL （如500ms）
​
2. 在主循环 while(1) 里不断判断：当前时间 - 上次翻转时间 ≥ 设置的间隔
​如果满足：更新 last_time 为当前时间，执行LED切换逻辑

