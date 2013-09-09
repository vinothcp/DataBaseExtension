DataBaseExtension
=================
















DataBaseExtension
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Threading.Tasks;

namespace ConsoleApplication8
{
    class Program
    {
        static void Main(string[] args)
        {
            StringBuilder QueryBuild = new StringBuilder();
            StringBuilder CompleteStringBuilder = new StringBuilder();
            string Query=string.Empty;
            while(true)
            {               
                Query = Console.ReadLine();                
                int Index = Query.LastIndexOf(";");
                if (Index != -1)
                {
                    QueryBuild.Append(Query);
                    string CompleteQuery = Convert.ToString(QueryBuild);
                    CompleteQuery = CompleteQuery.Trim();
                    string[] QuerySplit = CompleteQuery.Split(' ');
                    for (int i = 0; i < QuerySplit.Length; i++)
                    {
                        if (!QuerySplit[i].Equals(""))
                        {                            
                            QuerySplit[i] = QuerySplit[i].Trim();                            
                            QuerySplit[i] += " ";                            
                            CompleteStringBuilder.Append(QuerySplit[i]);
                        }
                        
                    }
                    if (CompleteQuery.Equals("exit"))
                    {
                        break;
                    }
                    else if (CompleteQuery.StartsWith("create"))
                    {
                        Create OCreate = new Create();
                        OCreate.ValidateQuery(Convert.ToString(CompleteStringBuilder));
                    }
                }
                else
                {                    
                    QueryBuild.Append(Query+" ");                    
                }                
            }
        }
    }
}
