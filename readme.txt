如何使用uterminal

该模拟终端，一般使用在 低端设备加串口中。

1.将uterminal加入工程中，一般不会有问题；
2.uterminal 使用malloc申请内存的函数，所以需要注意在低端设备中设置堆区稍微大一些；
3    #include <stdio.h>
    #include <stdlib.h>
    #include <stdint.h>
    #include <string.h>
  这是用到的外部的库，一般情况都有；


4.建立全局指针 CMD_NCB_ST *fs；
5.申请内存，建立对象 cmd_create；
6.申请回掉处理函数，cmd_register；
7.将中断接收处理函数放置在中断中 cmd_read_lines；
8.不用了就将申请的内存释放掉。

例子
CMD_NCB_ST *fs;
int main(void)
{ 
	
	cmd_create(&fs,printf,putc_,"robot:");
	cmd_register(fs,"ls",  "help0\n\r", ls);
	cmd_register(fs,"cd", "help1\n\r", cd);
	cmd_register(fs,"help", "help2\n\r", HelpCmdExeFun);
	cmd_register(fs,"heel", "hell all cmd\n\r", HelpCmdExeFun);
	cmd_register(fs,"helf", "helf all cmd\n\r", HelpCmdExeFun);
	cmd_register(fs,"helq", "helq all cmd\n\r", HelpCmdExeFun);
	cmd_register(fs,"hdff", "heeff all cmd\n\r", HelpCmdExeFun);
	cmd_register(fs,"hcdd", "hedddd all cmd\n\r", HelpCmdExeFun);
	cmd_register(fs,"hblp2", "heebb all cmd\n\r", HelpCmdExeFun);
	cmd_register(fs,"hblp1", "heelff all cmd\n\r", HelpCmdExeFun);
	while(1)
	{

	}
}

void USART1_IRQHandler(void)
{
	unsigned short int i;
	unsigned char temp;
	temp = temp;
	i = i;
	if(USART_GetITStatus(USART1, USART_IT_RXNE) != RESET)
	{ 
		cmd_read_lines(fs,USART1->DR);
		USART1->SR;
		return;	
	} 
	if(USART_GetITStatus(USART1, USART_IT_TXE) != RESET)
	{		
	    USART_ClearITPendingBit(USART1, USART_IT_TXE);
	}	 
}

