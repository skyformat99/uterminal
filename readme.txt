���ʹ��uterminal

��ģ���նˣ�һ��ʹ���� �Ͷ��豸�Ӵ����С�

1.��uterminal���빤���У�һ�㲻�������⣻
2.uterminal ʹ��malloc�����ڴ�ĺ�����������Ҫע���ڵͶ��豸�����ö�����΢��һЩ��
3    #include <stdio.h>
    #include <stdlib.h>
    #include <stdint.h>
    #include <string.h>
  �����õ����ⲿ�Ŀ⣬һ��������У�


4.����ȫ��ָ�� CMD_NCB_ST *fs��
5.�����ڴ棬�������� cmd_create��
6.����ص���������cmd_register��
7.���жϽ��մ������������ж��� cmd_read_lines��
8.�����˾ͽ�������ڴ��ͷŵ���

����
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

