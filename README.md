# 4-bit-Up-Counter-using-FSM

 module FSM_counter(clk, reset, din, z);
input wire clk,reset,din;
output reg [1:0] z;
reg [1:0] state;
parameter s0 = 2'b00, s1 = 2'b01, s2 = 2'b10, s3 = 2'b11;

always@(posedge clk)
begin
if (reset == 1)
   state <=s0;
   else
   state <= state;
  
end
   always@(posedge clk)
   begin  
 case(state)
 
   s0:begin
      if(din == 1)
      #10 state <= s1;
      else #10 state <=s0;   
   end
   
   s1:begin
         if(din == 1)
         #10 state <= s2;
         else #10 state <=s1;  
      end
      
      s2:begin
            if(din == 1)
            #10 state <= s3;
            else #10 state <=s2;   
         end
         
         s3:begin
               if(din == 1)
               #10 state <= s0;
               else #10 state <=s3;  
          end
          endcase
          end
          always@(posedge clk)
          begin
          #10 assign z = state;
          end
endmodule
