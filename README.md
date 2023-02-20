import java.util.*;
public class JobScheduling
{
	public static void main(String[] args)
	{
	Scanner sc = new Scanner(System.in);
	System.out.println("enter the number of jobs");
	int n = sc.nextInt();  // number of jobs
	Job[] jobs = new Job[n];
	for(int i=0;i<n;i++)
	{
	System.out.println("enter the start_time,end_time,profit");
	int start_time = sc.nextInt();
	int end_time = sc.nextInt();
	int profit = sc.nextInt();
	jobs[i] = new Job(start_time,end_time,profit);
	}
	
	Arrays.sort(jobs,new Comparator<Job>()
	{
	public int compare(Job j1,Job j2)
	{
	return j1.end_time - j2.end_time;
	}
	});
	
	int max_profit=0;
	int numberofjobspicked=0;
	int lastendtime=0;
	
	for(Job job:jobs)
	{
		if(job.start_time>=lastendtime)
		{
		max_profit = max_profit+job.profit;
		numberofjobspicked++;
		lastendtime = job.end_time;
		}
	}
	
	int numjobsleft=n-numberofjobspicked;
	int total_earning = 0;
	for(int i=numberofjobspicked;i<n;i++)
	{
	total_earning+=jobs[i].profit;
	}
	System.out.println("Task:"+numjobsleft);
	System.out.println("Earning:"+total_earning);
	}
}
	class Job
	{
	int start_time;
	int end_time;
	int profit;
	
	public Job(int start_time,int end_time, int profit)
	{
	this.start_time=start_time;
	this.end_time=end_time;
	this.profit=profit;
	}
	}

