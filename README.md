# Cost-estimation-and-budget-analysis-
class ProjectCost:
    def __init__(self):
        self.tasks = {}  # Dictionary to store task names and their costs

    def add_task(self, task_name, estimated_cost):
        """Add a task and its estimated cost"""
        self.tasks[task_name] = {'estimated_cost': estimated_cost, 'actual_cost': 0}

    def set_actual_cost(self, task_name, actual_cost):
        """Set the actual cost for a task"""
        if task_name in self.tasks:
            self.tasks[task_name]['actual_cost'] = actual_cost
        else:
            print(f"Task '{task_name}' does not exist.")

    def get_estimated_total(self):
        """Return the total estimated cost of the project"""
        total = sum(task['estimated_cost'] for task in self.tasks.values())
        return total

    def get_actual_total(self):
        """Return the total actual cost of the project"""
        total = sum(task['actual_cost'] for task in self.tasks.values())
        return total

    def compare_costs(self):
        """Compare the estimated and actual costs"""
        estimated = self.get_estimated_total()
        actual = self.get_actual_total()
        difference = actual - estimated
        return estimated, actual, difference

    def generate_report(self):
        """Generate a simple budget analysis report"""
        estimated_total, actual_total, difference = self.compare_costs()
        print("Project Budget Report")
        print(f"---------------------")
        print(f"Total Estimated Cost: ${estimated_total}")
        print(f"Total Actual Cost: ${actual_total}")
        print(f"Difference: ${difference}")
        print(f"---------------------")
        for task, costs in self.tasks.items():
            print(f"Task: {task}")
            print(f"  Estimated Cost: ${costs['estimated_cost']}")
            print(f"  Actual Cost: ${costs['actual_cost']}")
            print(f"---------------------")

# Example usage
project = ProjectCost()

# Add tasks with estimated costs
project.add_task("Design", 5000)
project.add_task("Development", 15000)
project.add_task("Testing", 3000)

# Set actual costs (after some progress in the project)
project.set_actual_cost("Design", 4500)
project.set_actual_cost("Development", 16000)
project.set_actual_cost("Testing", 2800)

# Generate a report
project.generate_report()
